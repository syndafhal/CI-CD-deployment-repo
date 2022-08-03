

    
 node {

    properties([
        pipelineTriggers([
        [$class: 'GenericTrigger',
            genericVariables: [
            [ key: 'name', value: '$.data.name' ],
            [ key: 'location', value: '$.data.path' ]
            ],
            token: '123',
            printContributedVariables: true,
            printPostContent: true,

        ]
        ])
    ]
              )


 
    

   

    stages {
        
        stage('Preparation') {
        steps{
        git branch: "main",
        url: 'https://github.com/syndafhal/Deployment.git'}
    }
    
        

        stage('Setup Environment for APICTL') {
            steps {
            environment {
               PATH = "/home/synda/Bureau/apictl:$PATH"}
    
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
        
   
}}
