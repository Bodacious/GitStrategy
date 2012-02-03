# Katana Code's Git Strategy

## Introduction

The purpose of this document is to define the strategy which all Katana Code employees and subcontractors must adhere to when working on Katana Code projects. 

The aim is to develop a uniform, coherent and effective solution. This document is not written in stone and can be updated as and when better approaches are discovered.

## Topic Branches

Each project must have a "primary" branch (usually **master**).

On website applications a **staging** and **production** branch may also be used to point to staging and production releases respectively. In this case, the **production** branch will be the "primary" branch.

### Creating Topic Branches

When making changes to the code, one must typically check out a *new* topic branch from the primary branch.

``` bash
$ git co -b feature/feature_name
```

When checking out an existing topic branch (continuing development of an existing feature) one must first rebase this branch on the primary branch.

``` bash
$ git co -b feature/existing
$ git rebase production
```

### Naming Topic Branches

Topic branches must be nested under one of the following categories:

* feature - A feature of the application is being developed. <br>e.g. **feature/comments**
* bug - A single bug is being corrected.<br>e.g. **bug/sign_in**
* refactor - A single file of the code is being refactored.<br>e.g. **refactor/user.rb**
* dev - The code is being modified to improve development.<br>e.g. **dev/upgrading_rails**. This includes:
    * Upgrading software versions
    * Replacing gems/libraries
    * Adding development tools such as macros for testing.
* copy - Some of the page copy in the application templates is being changed. <br> e.g. **copy/about_us**
* config - A configuration has changed.<br> e.g. **config/amazon_settings**
* design - Artwork, HTML or CSS is being changed to incorporate a new design. No behavioural changes may be made.<br> e.g. **design/sign_up_button**
* documentation - This should not be a nested branch. All documentation may be committed under **documentation** <br> NOTE - Documentation files should not be stored within the Git repository (see Ignore Files).

Topic branches may be sub-nested if doing so helps to explain the nature of the topic in more depth. e.g., **feature/api/session_management**

### Merging Topic Branches

When a topic branch is ready to be committed to the primary branch, one must first rebase the topic branch on the primary branch.

    $ git rebase master # while on topic

## Ignore Files

Each repository must have a `.gitignore` file. The following files/directories must be ignored where applicable.

    # ignore this to prevent tedious commits containing only bundle updates
    Gemfile.lock 
    # for web apps
    .DS_Store
    # for web apps
    tmp/ 
    # for web apps
    public/index.html 
    # for Ruby gems
    pkg/ 

## Versioning


