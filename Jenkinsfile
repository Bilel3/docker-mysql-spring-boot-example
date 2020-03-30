pipeline {
   agent any

   stages {
      
        stage('Pulling repo') {
            steps {
                git 'https://github.com/Bilel3/docker-mysql-spring-boot-example.git'
                    }
                }
      
        stage('maven install') {
                steps {
                    sh 'mvn clean install -Dmaven.test.skip=true'
                }
              }
      
           stage('Check code Quality') {
                steps {
                   sh 'mvn sonar:sonar'
                        }
                    }
      
        stage('Building Image') {
            steps {
                sh 'docker build . -t users-mysql'
                    }
                }
      
        stage('Running services') {
            steps {
                sh 'cd DockerCompose/'
                sh 'docker-compose up -d'
            }
         //  post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
           // success {
             //  archiveArtifacts 'target/*.jar'
              // sh 'mvn clean deploy'
            //}
           //}
          }

       }

}
