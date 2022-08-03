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
        git branch: "dev",
        url: 'https://github.com/chamilaadhi/poc-cicd-deployment-repo.git'
    }
    
    stage('Setup Environment for APICTL') {
        sh '''#!/bin/bash
        echo $location
        
        '''
    }}
