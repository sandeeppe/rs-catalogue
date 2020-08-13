pipeline {
    
    agent any
    
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
                sh 'tar -czf catalogue.tgz node_modules catalogue.js'
            }
        }

    }
    
}