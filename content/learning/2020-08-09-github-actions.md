---
title: "Building iOS Apps with Github Actions"
date: 2020-08-09T10:30:00-00:00
slug: github-actions
link: https://www.youtube.com/watch?v=ccrUi5QnUA0
subjects: ["ios"]
---

* Steps after pushing to master (where Github Actions comes in)
    1. Checkout the code
    2. Compile, archive and codesign it
    3. Upload to Apple
* Linux, macOS, Windows, ARM, and containers (note that macOS has a 10x premium on build times).
* Can be set to run every time code is pushed to a branch, or a pull request to a branch.
* Includes live logs.
* Built in secret store.
* Location: `.github/workflows/[filename].yml`.
* `uses:` is the step to checkout the repo.
* Provisioning
    1. Decrypt the p12 and provisioning profiles (generated in build step)
    2. Copy provisioning profiles to location xcode can access (same as double clicking)
    3. Add certificates from p12 to keychain
* Compile and archive with `xcodebuild` commands.
* Upload to Apple using `xcrun` command.
* Run Swiftlint and show issues inline (run on ubuntu since it’s just ruby code) - this is cool!