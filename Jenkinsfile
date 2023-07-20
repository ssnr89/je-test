pipeline {
    agent any
    stages {
        stage('For all branches') {
            steps {
                bat "npm ci"
                bat "npx nx test je-host"
            }
        }
        stage('Run for main branch') {
            when {
                branch 'main'
            }
            steps {
                bat "npx nx build je-host"
            }
        }
    }
}