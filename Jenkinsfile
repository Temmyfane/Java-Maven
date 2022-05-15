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
            buildJar()
        }
    }

    stage("build Docker Images") {
    	
        steps {
          echo "Building the MVN Project"
            buildDockerImage(dockerReg="erfanrider", imageTag="java-apps:1.4.0")
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