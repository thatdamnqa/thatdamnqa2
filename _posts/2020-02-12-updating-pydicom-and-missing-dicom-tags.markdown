---
layout: post
title:  "Updating PyDicom and missing dicom tags?"
date:   2020-02-12 00:00:00 +0000
categories: blog
tags: Python
---

As part of a bit of work updating PyDicomfrom 0.x to 1.x, I came across a number of AttributeErrors:
`AttributeError: 'FileDataset' object has no attribute 'ImagePathFilterTypeStackCodes'`

The Dicoms are the same, and the error message are always in the same format (with a missing Dicom tag that it could find before) so the problem must be with PyDicom.
(Note: this is assuming the tag isn't a private tag. This is also new behaviour: you can search for a Dicom by its ID instead of its name)

Turns out there's a change in PyDicom which removed a specific bit of code:

```
# Take "Sequence" out of name (pydicom < 0.9.7)
# e..g "BeamSequence"->"Beams"; "ReferencedImageBoxSequence"->"ReferencedImageBoxes"
# 'Other Patient ID' exists as single value AND as sequence so check for it and leave 'Sequence' in
if dictionaryVR(tag) == "SQ" and not s.startswith("OtherPatientIDs"):
    if s.endswith("Sequence"):
        s = s[:-8] + "s"
    if s.endswith("ss"):
        s = s[:-1]
    if s.endswith("xs"):
        s = s[:-1] + "es"
    if s.endswith("Studys"):
        s = s[:-2] + "ies"
return s
```

(inside `datadict.py` method `CleanName()` – lines 134-146 in the version we were using, for those who want to find it)

That means, if our code was looking for the attribute `ReferencedImageBoxSequence`, then you could also search for `ReferencedImageBoxes`, and they're both copies of the same Dicom tag data.

The fix? Unfortunately it's a labourous one: you need to go through the test code, see which ones work and which don't, and change them. This might be a task you can automate using grep, but it might also just be quicker to do it manually.