pipeline {

    agent any
    
    
environment {
        PATH = "/home/synda/Bureau/apictl:$PATH"
    }


    stages {
        
        stage('Preparation') {
            steps{
                git branch: "main",
                url: 'https://github.com/syndafhal/Deployment.git'

            }
        }

        stage('Setup Environment for APICTL') {
            steps {
                sh '''#!/bin/bash
                #rm /var/lib/jenkins/workspace/gitconfig
                #touch /var/lib/jenkins/workspace/gitconfig
                apictl set --vcs-config-path /var/lib/jenkins/workspace/gitconfig
                apictl remove env dev
                envs=$(apictl get envs --format "{{.Name}}")
                if [ -z "$envs" ]; 
                then 
                    echo "No environmen configured Setting dev environment.."
                    apictl add env dev --apim https://10.1.31.119:9443 
                else
                    echo "Environments :"$envs
                    if [[ $envs != *"dev"* ]]; then
                    echo "Dev environment is not configured. Setting dev environment.."
                    apictl add env dev --apim https://10.1.31.119:9443
                    fi
                fi
                apictl get envs
                '''
            }
        }
          stage('Deploy to Development Environment') {

            steps {
         sh '''#!/bin/bash

        # download the artifact from the artifact repository
        wget https://server2.jfrog.io/artifactory/repo/$location
        echo "ok"
        echo $data
        # derive param content name 
        fileName=$(echo $name | sed 's/\\(.*\\).zip/\\1 /')
        
        echo filename
        paramPath="DeploymentArtifacts_"$deploymentName
        deploymentName=$(echo $fileName | sed 's/\\(.*\\)_/\\1-/')
        echo "Param path :"$paramPath
       
        '''
                
       
      

      


      

        

            }
        }
       
    }}
