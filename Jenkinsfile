pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
		stage('Maven Build') {
            steps {
                sh 'mvn install '
            }
        }
        stage('Dockerfile') {
            steps {
                sh "ls -ltra"
            }
        }
         stage('dockert build') {
            steps {
                sh "docker build . -t tomcattes"
                
            }
        }
          stage('dockert run') {
            steps {
			
                sh "docker run -dit --name my-running-appdocker -p 80:8080  tomcattes "
                
            }
        }
        stage('test url ') {
            steps {
                sh 'curl -v http://192.168.29.248/annaApps/'
                
            }
        }
         stage('stop docker cont ') {
            steps {
                sh 'docker stop my-running-appdocker '
                
            }
        }
        stage('remove docker cont ') {
            steps {
                sh 'docker rm my-running-appdocker '
                
            }
        }
        
    }
}

