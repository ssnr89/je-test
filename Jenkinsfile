pipeline {
    agent any
    stages {
        stage('For all branches') {
            steps {
                bat "npm ci"
                //bat "npx nx test je-host"
            }
        }
        stage('Run for main branch') {
            when {
                branch 'main'
            }
            steps {
                bat "npx nx build je-host"
                bat "dir"
                withAWS(credentials:'aws-credentials', region:'ap-south-1') {
                    s3Delete(bucket:'je-int-deploy')
                    // s3Upload(bucket:"je-int-deploy", includePathPattern:'**/*', workingDir:'dist/apps/je-host')
                }
            }
        }
    }
}