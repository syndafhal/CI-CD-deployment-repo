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
                    apictl add env dev --apim https://10.1.31.188:9443 
                else
                    echo "Environments :"$envs
                    if [[ $envs != *"dev"* ]]; then
                    echo "Dev environment is not configured. Setting dev environment.."
                    apictl add env dev --apim https://10.1.31.188:9443
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
        wget https://server2.jfrog.io/artifactory/repo/PizzaShackAPI-1.0.0/1.0.0/PizzaShackAPI_1.0.0.zip 
        paramPath=DeploymentArtifacts_PizzaShackAPI-1.0.0
        echo "Param path :"$paramPath
        ech $location

       
        # login to the dev environment
        apictl login dev -u admin -p admin -k
        # import the artifact
         message=$(apictl import api -f PizzaShackAPI-1.0.0 --params DeploymentArtifacts_PizzaShackAPI-1.0.0 -e dev --update -k)
        
    


        '''
                
       
      

      


      

        

            }
        }
       
    }}
