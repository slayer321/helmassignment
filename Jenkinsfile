pipeline {
    agent any
    environment {
        SECRET_FILE_ID = credentials('kubeconfig')
      }
    

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage("checkout Repo") {
            steps {
                    checkout scm
                }
        }

        stage('dependency') {
            steps {

               sh "helm dependency update"
                
            }

           
        }
          stage('lint') {
            steps {
                sh "helm lint ."
               }

           
        }
              stage('package') {
            steps {

               
               sh "helm package ."
               
                
            }

           
        }
        stage('install') {
            steps {
               sh 'helm --kubeconfig $SECRET_FILE_ID install helmproject .'
        }
           }
        
   
    }

}