---
layout: post
title:  "Using PHP composer with multiple versions of PHP"
date:   2018-06-05 00:00:00 +0000
categories: blog
---

This problem has hurt me a few times while updating this (Drupal) website, so I'm mostly posting this braindump for myself. But, it might help somebody else.

The main cause of my problem is I commit composer's /vendor directory into git. (Why do I do this? [Here's an article which explains better than I could on why you may want to commit the vendor directory](https://www.codeenigma.com/build/blog/do-you-really-need-composer-production). In short, I find it more helpful to have all the code in git, for easier deployment. But, I may change my mind in the future, given these recent problems I've been having).

Anyway. My computer (which I use to update Drupal for my site) runs php 7.1, and my server is still running php 7.0. This causes problems in terms of dependencies, when composer assumes I'll be using php 7.1, so I inevitably get code errors.

I solved this problem by adding a few lines to my composer.json:

    "config": {
      "sort-packages": true,
        "platform": {
            "php": "7.0"
        }
      },
      
Which worked fine, until a dependency update meant I didn't have the correct php version. This caused composer to update to an older version of Drupal (Drupal 8.4.8 rather than Drupal 8.5.3), and this output when I forced composer to update to Drupal 8.5.x:


    Problem 1
        - drupal/core 8.6.x-dev requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.x-dev requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.3 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.2 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.1 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.0-rc1 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.0-beta1 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.0-alpha1 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - drupal/core 8.5.0 requires php ^5.5.9|>=7.0.8 -> your PHP version (7.1.7) overridden by "config.platform.php" version (7.0) does not satisfy that requirement.
        - Installation request for drupal/core ~8.5 -> satisfiable by drupal/core[8.5.0, 8.5.0-alpha1, 8.5.0-beta1, 8.5.0-rc1, 8.5.1, 8.5.2, 8.5.3, 8.5.x-dev, 8.6.x-dev].
(As a side-note, my initial reaction was to try `composer update  --with-dependencies --ignore-platform-reqs`, which worked, but of course meant that composer wasn't downloading dependencies for php 7.0, which is what I wanted).

Turns out, as I had php 7.0.30 installed on my server, I could just update my composer.json to update the platform tag, and do a regular `composer update`. Which did the job, for now. I'll inevitably need to update my server to php 7.2, eventually.

**So, tl;dr, there's two things I need to remember:**

* If I commit my composer vendor folder, I need to **ensure that both my work computer and my server have exactly the same version of php on both machines**
* If not, then to ensure code works properly, I need to add a platform tag into my composer.json file, ensuring it is accurate, including fix bug versions. And remember **never to use `--ignore-platform-reqs`**. It will mean that composer will update, but to the wrong version.
