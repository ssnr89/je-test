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
                sh """
                echo "Building Artifact from Master branch"
                """

                sh """
                echo "Deploying Code from Master branch"
                """
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