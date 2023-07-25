pipeline {
    agent any
    stages {
        stage('Test and Code quality') {
            steps {
                bat "npm ci"
                bat "npx nx test je-host"
            }
        }
        stage('Build and deploy') {
            when {
                branch 'main'
            }
            stages {
                stage('Build in integration') {
                    steps {
                        bat "npx nx build je-host"
                    }
                }
                stage('Deploy to integration') {
                    steps {
                        withAWS(credentials:'aws-credentials', region:'ap-south-1') {
                            s3Delete(bucket:'je-int-deploy', path:'/')
                        }
                        withAWS(credentials:'aws-credentials', region:'ap-south-1') {
                            s3Upload(bucket:"je-int-deploy", includePathPattern:'**/*', workingDir:'dist/apps/je-host')
                        }
                    }
                }
                stage('Deploy to prod') {
                    steps {
                        timeout(time: 2, unit: "DAYS") {
                            input message: 'Do you want to approve the deployment?', ok: 'Yes'
                        }
                        echo "init deploy"   
                    }
                }
            } 
        }
    }
}