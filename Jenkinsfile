pipeline {

    agent {
        label 'build'
    }

    environment {
          JAVA_HOME = tool 'JDK-17'
          M2_HOME = tool 'MAVEN-3.8.8'
    }


    stages {
        stage('Clone Repository') {
            steps {
                // Cloning the repository
                git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
    
        stage('Check Versions') {
            steps {
                sh '${JAVA_HOME}/bin/java -version'
                sh '${M2_HOME}/bin/mvn -version'
                
            }
        }
        stage('Build'){
            steps {
            // mail bcc: '', body: 'Build Started', cc: '', from: '', replyTo: '', subject: 'Build Started', to: 'moiz.bigdata@gmail.com'
                script {
                 sh '${M2_HOME}/bin/mvn clean package'
                }  
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts '**/target/*.jar'
            // mail bcc: '', body: 'Build Completed', cc: '', from: '', replyTo: '', subject: 'Build Completed', to: 'moiz.bigdata@gmail.com'
            }
            // post {
            //     always {
            //         archiveArtifacts '**/target/*.jar'
            //     }
            //     success {
            //         junit '**/target/surefire-reports/*.xml'
            //     }
            // }

        }
        stage('Tests'){
            steps {
                sh 'echo "mvn test"'
            }
            // script {
            //      junit '**/target/surefire-reports/*.xml'
            // }  
        }

    }
}



