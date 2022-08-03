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
    }}
