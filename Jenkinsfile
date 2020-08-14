pipeline {
    
    agent any

    environment {
        NEXUS = credentials('NEXUS')
        MAJOR_VERSION=1
        ITERATION_NUMBER=2
    }
    
    stages { 
        stage('NPM Install') {
            steps {
                sh label: '', script: '''
                  npm install
                '''
            }
        }

        stage('Archive') {
            steps {
                sh 'tar -czf catalogue.tgz node_modules catalogue.js package.json'
            }
        }

        stage('Upload Artifacts') {
            steps {
                sh '''
                VERSION="${MAJOR_VERSION}.${ITERATION_NUMBER}.${BUILD_NUMBER}"
                mv catalogue.tgz catalogue-${VERSION}.tgz
                curl -v -u ${NEXUS_USR}:${NEXUS_PSW} --upload-file catalogue-${VERSION}.tgz http://3.234.236.173:8081/repository/catalogue/catalogue-${VERSION}.tgz
                '''
            }
        }

    }
    
}