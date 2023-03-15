Demo - demonstrates an application and tests
This is an application by Coveros to demonstrate good software practices. As we say in agile... Working software over comprehensive documentation ... but that doesn't mean we can't have pretty good documentation too.

Quick Start:
Install Java if you don't already have it.
Clone or download this repo. (if you download, unzip the file to a directory.)
On the command line in the top directory of this repo, run gradlew apprun
Visit the application with your browser at http://localhost:8080/demo
Summary:
Demo consists of a simple web application and tests. Its goal is to provide an environment suitable for demonstration and practice in valuable development techniques. Some of the techniques exemplified are:

Unit tests developed by TDD using Junit as a driver and Mockito for mocks, with coverage reports.
UI tests using multiple frameworks
BDD tests using gherkin
Cucumber tests, with reports
Behave UI tests that use Selenium web driver.
Integration tests that test the H2 database
Database versioning, with Flyway
Security analysis using DependencyCheck
Hot-swap code with Gretty
Enhanced type system using Checker Framework
See its architecture
Its essential goals:

Just works, any platform.
As simple as possible
Minimal system requirements
Fast and easy to install and to run
High test coverage
Multiple business domains
Easy to maintain and improve
Well documented
High performance
Illustrates maximum number of techniques
Easy to get up to speed
Table of contents:
Optional dependencies
Chromedriver installation notes
Python installation notes
To build and run tests
To run the application
To run API and UI tests
Summary of relevant Gradle commands
The whole shebang - CI/CD pipeline
Optional Dependencies
If you want API testing and Selenium testing, you will need to visit these links and download / install the applications found there.

Python
Chromedriver
Chrome internet browser
Chromedriver installation notes
make sure that the Chromedriver executable is installed in one of the directories that is on your path. To see your path, type the following in a command line:

on Windows:

echo %PATH%  
On Mac/Linux:

echo $PATH
If you run the command, chromedriver on the command line, you should get a result similar to this:

Starting ChromeDriver ...
Python installation notes
Python can be downloaded here

To run API tests and Selenium tests, an easy way to handle its dependencies is to use pipenv. To get this installed, first download get-pip.py, and run the following on the command line:

python get-pip.py
Then,

pip install pipenv
And in the demo directory,

pipenv install   
To build and run tests:
On the command line, run the following:

On Mac/Linux

./gradlew check
On Windows

gradlew check
To run the web application:
On the command line, run the following:

On Mac/Linux

./gradlew apprun
On Windows

gradlew apprun
Then, head to http://localhost:8080/demo

To run API and UI tests:
Note: The app has to be already running for these tests to pass, and you need to have installed [Python] and [Chromedriver].

In a new terminal, separate from the one where the server is running, run the following:

On Mac/Linux

./gradlew runAllTests
On Windows

gradlew runAllTests    
Summary of relevant Gradle commands
gradlew coveros - show a cheat sheet of commands for Demo

gradlew apprun - runs the application

gradlew check - runs all tests possible with only dependency being Java 8. No need for app to be running.

gradlew runAllTests - runs the whole set of tests**

gradlew clean - cleans build products and installs pre-push hook. (see the file in this directory, pre-push)

gradlew runBehaveTests - runs the UI tests**

gradlew runApiTests - runs the API tests**

gradlew generateCucumberReport - runs cucumber and creates a nice-looking HTML report

gradlew pitest - runs mutation testing (see http://pitest.org/)

gradlew dependencyCheckAnalyze - analyzes security reports for the dependencies of this project. See https://www.owasp.org/index.php/OWASP_Dependency_Check

gradlew sonarqube - runs static analysis using SonarQube. Sonarqube must be running - check http://localhost:9000

gradlew integrate - runs the database integration tests

gradlew startH2Console - Starts a console to examine the H2 database file. (user and password are empty, URL to use is jdbc:h2:./build/db/training)

gradlew <task 1>... taskTree - a utility that will show the task tree for a particular task

** Requires the app to be running (usually in another terminal) and all optional dependencies installed.

The whole shebang - a CI/CD pipeline
Details on building out a CI/CD pipeline are found in the "docs/ci_and_cd" directory. For example, to set it all up on a local Windows box

Features of the pipeline:
A fully functioning and documented demonstration CI/CD pipeline using Jenkins.
BDD tests run with a report generated
Static analysis quality-gating using SonarQube
UI tests running on Chrome
Performance testing with Jmeter
Security analysis with OWASP's "DependencyCheck"
Complex commands wrapped simply using Gradle
Mutation testing with Pitest
Javadocs built
Screenshots:
