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
                apictl remove env dev
                envs=$(apictl get envs --format "{{.Name}}")
                if [ -z "$envs" ]; 
                then 
                    echo "No environment configured. Setting dev environment.."
                    apictl add env dev --apim https://10.1.31.188:9443 
                else
                    echo "Environme10.1.31.18810.1.31.188nts :"$envs
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
        wget https://server2.jfrog.io/artifactory/repo/PetstoreAPI/1.0.0/SwaggerPetstore_1.0.0.zip 
        paramPath=DeploymentArtifacts_SwaggerPetstore-1.0.0
        echo "Param path :"$paramPath

       
        # login to the dev environment
        apictl login dev -u admin -p admin -k
        # import the artifact
        message=$(apictl import api -f SwaggerPetstore --params $paramPath -e dev --update -k)
    


        '''
                
       
      

      


      

        

            }
        }
       
    }}
