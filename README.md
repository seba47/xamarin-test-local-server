
# Xamarin Test Box for Windows

![](https://img.shields.io/badge/version-1.0-green.svg?style=flat)
![](https://img.shields.io/badge/os-Windows-yellow.svg?style=flat)
[![Twitter: @seba47](https://img.shields.io/badge/contact-@seba47-blue.svg?style=flat)](https://twitter.com/seba47)

Run Xamarin UI and Unit(xunit) Tests in Windows with only 2 clicks. Pull from your repo, build projects and run tests.
<br/>
<br/>
**Platform Support**

|Platform|Available|
| ------------------- | :-----------: |
|Xamarin.Android|![alt text](https://www.pedshoes.com/images/general/greenCheck50x50Transparent.png)|
|Xamarin.iOS|![alt text](http://i4ultimate.com/alertemails/warning-icon-orange.png)|

<br/>

## Requirements

 - MsBuild (included with Visual Studio)
 - Xamarin Solution with UI Test Project and Unit Test Projects(with xunit) within a git repository in your file system.
 - UITest project with a real device configured (e.g: check Test.Cs section in http://sebacabrera.com/automated-xamarin-ui-tests-and-recorder/)
 - Add xunit console package in your UnitTest project - by Package
   Manager in VS or https://www.nuget.org/packages/xunit.runner.console
 - NUnit Console for Windows - http://nunit.org/download/
 - Git Bash - https://git-for-windows.github.io/

<br/>

## Pre-Configuration

#### If you have never compile your solution on this machine, do it!
NuGet packages should be in the file system so be sure they were restored after building. [Enabling and disabling package restore](https://docs.microsoft.com/en-us/nuget/consume-packages/package-restore#enabling-and-disabling-package-restore).

#### Git Bash
If you have not used the bash, please login with your credentials because they will be needed later to get the last version of the tests.

#### NUnit Console
Give read/write permission to TestResult.xml (located into NUnit console folder) 

#### xUnit doesn´t need configuration

<br/>

## Setup

Complete your solution path in **pull-git-repo.sh**
```bash
...
cd /e/Projects/MyProject
...
```

<br/>

Complete project name and paths in **StartTesting.bat**
```bash
...
REM *** VARs declarations - REQUIRED! ***
SET projectName=MyProject

SET androidProjectFilePath=E:\Projects\MyProject\MyProject\MyProject.Droid\MyProject.Droid.csproj

SET xunitPath=E:\Projects\MyProject\packages\xunit.runner.console.2.2.0\tools
SET unitTestProjectFilePath=E:\Projects\MyProject\Test\MyProject.UnitTest\MyProject.UnitTest.csproj
SET unitTestReleaseLibraryPath=E:\Projects\MyProject\Test\MyProject.UnitTest\bin\Release\MyProject.UnitTest.dll

SET nunitPath=C:\Program Files (x86)\NUnit.org\nunit-console
SET uITestProjectFilePath=E:\Projects\MyProject\Test\MyProject.UITest\MyProject.UITest.csproj
SET uiTestReleaseLibraryPath=E:\Projects\MyProject\Test\MyProject.UITest\bin\Release\MyProject.UITest.dll
...
```

<br/>

## Running Test Process

Open Run.bat and the process will be the next:

* Git Pull on the current branch of the project
* Build Android project (If your git pulls take much longer time,you can increase the waiting time for compiling Android: into Run.bat - line 10)
* Build UnitTest project
* Build UITest project
* Open xUnit Console and run Unit tests
* Run UI tests in the connected device

<br/>

## Clarifications

This tool works with only one solution. You should create folders with those scritps as solutions you have.
  
Based on the requirement number 3, UI tests will run in one physical device (previously configured in the UI Test project).

<br/>

## Version history

*1.0* (September 07, 2017)

* First version which shoulb be run manually in windows. It pulls the code, builds the projects and then runs unit tests and ui tests in your connected Android device.

<br/>

## Working on

*  Run Unit tests created with NUnit
*  Restore NuGet Packages
*  Support for multiple Visual Studio solutions
*  Run UI tests in iOS device
*  Mac support
*  Run UI tests in multiple connected devices.
*  Continuous Integration with GitHub Repos using WebHooks and Node.js


<br/>

## Contributions
Feel free to add improvements and all stuffs that help us to get a better testing process. Contact me if you have suggestions.
