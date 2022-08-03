pipeline {

    agent any
    
    
environment {
        PATH = "/home/synda/Bureau/apictl:$PATH"
    }


    stages {
        
        stage('Preparation') {
            steps{
                git branch: "main",
                url: 'https://github.com/chamilaadhi/poc-cicd-deployment-repo.git'

            }
        }

        stage('Setup Environment for APICTL') {
            steps {
                sh '''#!/bin/bash
                #rm /var/lib/jenkins/workspace/gitconfig
                #touch /var/lib/jenkins/workspace/gitconfig
                apictl set --vcs-config-path /var/lib/jenkins/workspace/gitconfig
                envs=$(apictl get envs --format "{{.Name}}")
                if [ -z "$envs" ]; 
                then 
                    echo "No environment configured. Setting dev environment.."
                    apictl add env dev --apim https://10.1.31.188:9443 
                else
                    echo "Environments :"$envs10.1.31.18810.1.31.188
                    if [[ $envs != *"dev"* ]]; then
                    echo "Dev environment is not configured. Setting dev environment.."
                    apictl add env dev --apim https://10.1.31.188:9443 
                    fi
                fi
                '''
            }
        }
         stage('Deploy to Development Environment') {

            steps {
         sh '''#!/bin/bash

        # download the artifact from the artifact repository
        wget https://server2/artifactory/repo/$location

      

        '''

            }
        }
    }}
