#!/usr/bin/env groovy

@Library('Jenkins-shared-library')
def gv
pipeline {
  agent any
    tools {
        maven "Maven-Runner"
    }
  stages {
    stage("init") {
      steps {
            echo "Initializing the preparations"
            script {
                gv = load 'script.groovy'
            }
      }
    }

    stage("Build Jar") {
        steps {
            echo "Building the Maven Project"
            buildJar "erfanrider" "java-apps:1.5.0"
        }
    }


    stage("build Docker Images") {
        steps {
          echo "Building the MVN Project"
            buildDockerImage()
         }
    }
    
    stage("deploy") {
      steps {
        echo "Deploying the apps"
        script {
          gv.deploy()
      }
      }
    }
  }
}