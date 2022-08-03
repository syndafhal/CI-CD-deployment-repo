
    
    
environment {
        PATH = "/home/synda/Bureau/apictl:$PATH"
    }

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




    stage('Preparation') {
        git branch: "main",
        url: 'https://github.com/syndafhal/Deployment.git'
    }
    
    stage('Setup Environment for APICTL') {
        sh '''#!/bin/bash
        envs=$(apictl get envs --format "{{.Name}}")
        if [ -z "$envs" ]; 
        then 
            echo "No environment configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
        else
            echo "Environments :"$envs
            if [[ $envs != *"dev"* ]]; then
            echo "Dev environment is not configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
            fi
        fi
        '''
    }

    stage('Deploy to Development Environment') {
            
        sh '''#!/bin/bash

        # download the artifact from the artifact repository
        wget https://server2/artifactory/repo/$location

        # derive param content name 
        fileName=$(echo $name | sed 's/\\(.*\\).zip/\\1 /')
        deploymentName=$(echo $fileName | sed 's/\\(.*\\)_/\\1-/')
        paramPath="DeploymentArtifacts_"$deploymentName
        echo "Param path :"$paramPath

        # login to the dev environment
        apictl login dev -u admin -p admin -k
        # import the artifact
        message=$(apictl import api -f $name --params $paramPath -e dev --update -k)
        if [ "$message" = "Successfully imported API." ]; then
            echo "Successfully imported API."
        else
            echo $message
        fi
        rm $name

        '''
        
    }
     
}
}pipeline {

    agent any
    
    
environment {
        PATH = "/home/synda/Bureau/apictl:$PATH"
    }

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




    stage('Preparation') {
        git branch: "main",
        url: 'https://github.com/syndafhal/Deployment.git'
    }
    
    stage('Setup Environment for APICTL') {
        sh '''#!/bin/bash
        envs=$(apictl get envs --format "{{.Name}}")
        if [ -z "$envs" ]; 
        then 
            echo "No environment configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
        else
            echo "Environments :"$envs
            if [[ $envs != *"dev"* ]]; then
            echo "Dev environment is not configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
            fi
        fi
        '''
    }

    stage('Deploy to Development Environment') {
            
        sh '''#!/bin/bash

        # download the artifact from the artifact repository
        wget https://server2/artifactory/repo/$location

        # derive param content name 
        fileName=$(echo $name | sed 's/\\(.*\\).zip/\\1 /')
        deploymentName=$(echo $fileName | sed 's/\\(.*\\)_/\\1-/')
        paramPath="DeploymentArtifacts_"$deploymentName
        echo "Param path :"$paramPath

        # login to the dev environment
        apictl login dev -u admin -p admin -k
        # import the artifact
        message=$(apictl import api -f $name --params $paramPath -e dev --update -k)
        if [ "$message" = "Successfully imported API." ]; then
            echo "Successfully imported API."
        else
            echo $message
        fi
        rm $name

        '''
        
    }
     
}
}pipeline {

    agent any
    
    
environment {
        PATH = "/home/synda/Bureau/apictl:$PATH"
    }

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




    stage('Preparation') {
        git branch: "main",
        url: 'https://github.com/syndafhal/Deployment.git'
    }
    
    stage('Setup Environment for APICTL') {
        sh '''#!/bin/bash
        envs=$(apictl get envs --format "{{.Name}}")
        if [ -z "$envs" ]; 
        then 
            echo "No environment configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
        else
            echo "Environments :"$envs
            if [[ $envs != *"dev"* ]]; then
            echo "Dev environment is not configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
            fi
        fi
        '''
    }

    stage('Deploy to Development Environment') {
            
        sh '''#!/bin/bash

        # download the artifact from the artifact repository
        wget https://server2/artifactory/repo/$location

        # derive param content name 
        fileName=$(echo $name | sed 's/\\(.*\\).zip/\\1 /')
        deploymentName=$(echo $fileName | sed 's/\\(.*\\)_/\\1-/')
        paramPath="DeploymentArtifacts_"$deploymentName
        echo "Param path :"$paramPath

        # login to the dev environment
        apictl login dev -u admin -p admin -k
        # import the artifact
        message=$(apictl import api -f $name --params $paramPath -e dev --update -k)
        if [ "$message" = "Successfully imported API." ]; then
            echo "Successfully imported API."
        else
            echo $message
        fi
        rm $name

        '''
        
    }
     
}
}
    
    
environment {
        PATH = "/home/synda/Bureau/apictl:$PATH"
    }

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




    stage('Preparation') {
        git branch: "main",
        url: 'https://github.com/syndafhal/Deployment.git'
    }
    
    stage('Setup Environment for APICTL') {
        sh '''#!/bin/bash
        envs=$(apictl get envs --format "{{.Name}}")
        if [ -z "$envs" ]; 
        then 
            echo "No environment configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
        else
            echo "Environments :"$envs
            if [[ $envs != *"dev"* ]]; then
            echo "Dev environment is not configured. Setting dev environment.."
            apictl add env dev --apim https://10.1.31.188:9443  -k
            fi
        fi
        '''
    }


     
}

