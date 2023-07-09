pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Master Branch Deploy Code') {
            when {
                branch 'main'
            }
            steps {
                bat "npm ci"
                bat "npx nx build je-host"
                bat "npx nx test je-host"
            }
        }
        // stage('Develop Branch Deploy Code') {
        //     when {
        //         branch 'develop'
        //     }
        //     steps {
        //         sh """
        //         echo "Building Artifact from Develop branch"
        //         """
        //         sh """
        //         echo "Deploying Code from Develop branch"
        //         """
        //    }
        // }
    }
}