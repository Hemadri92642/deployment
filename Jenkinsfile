
pipeline {
    agent any
    parameters {
        
      //  booleanParam(name: "TEST_BOOLEAN", defaultValue: true, description: "Sample boolean parameter")
    
        //password(name: "TEST_PASSWORD", defaultValue: "SECRET", description: "Sample password parameter")
        
        choice(name: "environment", choices: ["production", "qa", "development"], description: "Sample multi-choice parameter")
        
        string(name: "branch", defaultValue: "development", trim: true, description: "Sample string parameter")
        
        choice(name: "datacent", choices: ["Bangalore", "HYD"], description: "Sample multi-choice parameter")
        
        string(name: "mavenbuild", defaultValue: "mvn install", trim: true, description: "Sample string parameter")
        string(name: "dockerport", defaultValue: "8080", trim: true, description: "Sample string parameter")
        
    }
    stages {
        stage("environment") {
            steps {
               // echo "Build stage."
                echo "environment = $params.environment"
            }
        }
         stage("branch") {
            steps {
               // echo "Build stage."
                echo "Branch = $params.branch"
            }
        }
        stage("datacent") {
            steps {
               // echo "Build stage."
                echo "datacent = $params.datacent"
            }
        }
        
        stage("maven build") {
            steps {
               // echo "Build stage."
                echo "mavenbuild = $params.mavenbuild"
		    sh "$params.mavenbuild"
            }
        }
        stage('Dockerfile') {
            steps {
              sh "ls -ltra"
              echo "Dockerfile"
            }
        }
         stage('docker build') {
            steps {
               sh "docker build . -t $params.environment"
               echo "docker build"
                
            }
        }
        
        stage("dockerport") {
            steps {
               // echo "Build stage."
                echo "dockerport = $params.dockerport"
            }
        }
        stage('dockert run') {
            steps {
			
                sh "docker run -dit --name $params.environment -p 80:$params.dockerport  $params.environment "
               //echo  "docker run -dit --name my-running-appdocker -p 80: $params.dockerport  tomcattes "
                 sleep 30 // seconds  
            }
        }
     
    }
}
