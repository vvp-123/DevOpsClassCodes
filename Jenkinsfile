#! /usr/bin/env groovy
import java.net.URL
import hudson.model.*
node{
    stage('git checkout'){
        git 'https://github.com/vvp-123/DevOpsClassCodes.git'
    }
    stage('compile'){
        withMaven(maven:'trainingmaven'){
            sh "mvn compile"
        }
    }
    stage('test'){
        try{
          withMaven(maven:'trainingmaven'){
            sh "mvn test"
          }  
        } finally{
            junit "target/surefire-reports/*.xml"
        }
    }
    stage('package'){
        withMaven(maven:'trainingmaven'){
            sh "mvn package"
        }
    }
}
