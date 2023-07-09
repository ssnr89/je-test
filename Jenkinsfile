pipeline {
    agent any
    stages {
        stage('Master Branch Deploy Code') {
            when {
                branch 'main'
            }
            steps {
                bat "npm ci"

                bat "npx nx build"
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