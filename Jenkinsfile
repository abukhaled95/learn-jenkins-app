pipeline {
    agent any

    environment {
        NETLIFY_SITE_ID = '323777a4-ec05-4c03-bb3e-5f1effddfe56'
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
    }

    stages {

        stage('Deploy staging') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo 'Deploying staging...
                '''
            }
        }

        stage('Approval') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    input 'Ready to deploy?'
                }
            }
        }

        stage('Deploy prod') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                   echo 'Deploying prod...'
                '''
            }
        }

    }

}