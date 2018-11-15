##
## https://www.linkedin.com/pulse/how-use-reactjs-java-web-applications-edward-mostrom/
##
## Refrence Project JavaReact
## Sample project incorporating React in a Java web appliation
## git clone https://github.com/emmostrom/JavaReact.git

## Purpose
* Incorporate React into a Java web application while still using standard Maven build commands for everything.
* When using "mvn jetty:run" include Hot Module Reloading so changes take effect immediately without restarting server or refreshing browser page.
* When using "mvn package" minimize all .js and .css files and include them in the .war file
* Require no changes to server side files (like web.xml) to support development mode
## Node is the Javascript runtime environment and is equivalent to the JRE for Java
## NPM is the Node Package Manager responsible for downloading and installing Javascript libraries much like Maven handles Java dependencies.
## Webpack is a Javascript application that is responsible for compiling and packaging web related resources into the final files that can be included into web pages
## The webpack-dev-server is a similar application that hosts the files and changes from its own server for hot reloading of resources.
## The frontend-maven-plugin will do the following:
##    1. will download Node and NPM into the node dir of the Java project
##    2. will download all of the javascript libs (inclding webpack) defined in the project.json into the the node_modules dir
##    3. The plugin can also run Webpack nd build final resources files as defined in the webpack.config.js file
## To enable hot reloading several things need to change when running in development.  Instead of using the frontend-maven-plugin
##      to run Webpack, the gmaven-plugin is used to run a simple Groovy script.  This Groovy script checks for jetty:run as a
##      Maven argument and instead of running webpack, it runs the webpack-dev-server.

## Requirements
* Java 7
* Maven 3.2

## Get Started

```
## git clone https://github.com/javaugi/reactwithmaven.git
## cd reactwithmaven
## mvn jetty:run

## Open browser to http://localhost:8080/reactWithMaven


edit src/main/jsx/Hello.jsx and change `Hello {this.props.who}` to `Good Bye {this.props.who}` and save file.  The browser should automatically show the new change.

Changes to .less files will automatically get picked up as well.

## Server Side Rendering

## See the SSR branch which requires Java 8 : https://github.com/emmostrom/JavaReact/tree/SSR
