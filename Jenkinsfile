pipeline {
    agent any

    stages {
        stage('Cloning Git Repository') {
            steps {
                git branch: 'qa', url: 'https://github.com/yazber-utpl/pruebas-jenkis.git'
            }
        }
        
        stage('Building Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('Building Application') {
            steps {
                sh '''
                # docker stop webapp_ctr        
                docker run --rm -d -p 3001:3000 --name webapp_ctr-qa webapp:${BUILD_NUMBER}
            '''        
            }
        }   
    }
}
