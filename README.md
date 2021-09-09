action-xcodebuild
=================

[![Issues](http://img.shields.io/github/issues/macmade/action-xcodebuild.svg?logo=github)](https://github.com/macmade/action-xcodebuild/issues)
![Status](https://img.shields.io/badge/status-active-brightgreen.svg?logo=git)
![License](https://img.shields.io/badge/license-mit-brightgreen.svg?logo=open-source-initiative)  
[![Contact](https://img.shields.io/badge/follow-@macmade-blue.svg?logo=twitter&style=social)](https://twitter.com/macmade)
[![Donate-Paypal](https://img.shields.io/badge/donate-paypal-pink.svg?logo=github-sponsors&style=social)](https://paypal.me/xslabs)

### About

GitHub Action for xcodebuild.

**Usage**:

    - uses: macmade/action-xcodebuild@v1.0.0

**Matrix configuration**:

  - **scheme**: `String`  
    The Xcode scheme on which to perform actions.  
    
  - **configuration**: `String`  
    The Xcode configuration to use (eg. `Debug`, `Release`).  
    
  - **project**: `String`  
    The Xcode project on which to perform actions.  
    
  - **build**: `Integer`  
    `0` or `1`: whether to build the project.
    
  - **analyze**: `Integer`  
    `0` or `1`: whether to run static analysis on the project.
    
  - **test**: `Integer`  
    `0` or `1`: whether to build and run configured unit tests.
    
  - **info**: `Integer`  
    `0` or `1`: whether to print various Xcode related informations.
    
  - **destination**: `String`  
    The Xcode destination device (eg `platform=macOS`).  
    
**Complete example**:

    name:   ci
    on:     [push]
    jobs:
        ci:
            runs-on: macos-latest
            strategy:
                matrix:
                    run-config:
                        - { scheme: 'macOS App', configuration: 'Debug',   project: 'App.xcodeproj', build: 1, analyze: 1, test: 1, info: 1, destination: 'platform=macOS' }
                        - { scheme: 'iOS App',   configuration: 'Release', project: 'App.xcodeproj', build: 1, analyze: 0, test: 0, info: 1, destination: 'platform=iOS Simulator,name=iPhone 12' }
            steps:
                - uses: actions/checkout@v1
                - uses: macmade/action-xcodebuild@v1.0.0

License
-------

Project is released under the terms of the MIT License.

Repository Infos
----------------

    Owner:          Jean-David Gadina - XS-Labs
    Web:            www.xs-labs.com
    Blog:           www.noxeos.com
    Twitter:        @macmade
    GitHub:         github.com/macmade
    LinkedIn:       ch.linkedin.com/in/macmade/
    StackOverflow:  stackoverflow.com/users/182676/macmade
