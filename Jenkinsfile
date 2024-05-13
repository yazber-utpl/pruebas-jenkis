pipeline {
    agent any

    stages {
        stage('Cloning Git Repository') {
            steps {
                git branch: 'dev', url: 'https://github.com/yazber-utpl/pruebas-jenkis.git'
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
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
            '''        
            }
        }   
    }
}
