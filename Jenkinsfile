pipeline {
    agent any

    tools {
        // Make sure you have configured Maven in Jenkins Global Tool Configuration with this exact name
        maven 'Maven'
        jdk 'JDK-21'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Checkout your repo's main branch
                git branch: 'main', url: 'https://github.com/Sabeshragav/jenkins-java-2'
            }
        }

        stage('Build with Maven') {
            steps {
                // Clean and build the Maven project, fail build on error
                bat 'mvn clean package'  // -B for batch mode (better Jenkins logs)
            }
        }

        // stage('Archive Artifact') {
        //     steps {
        //         // Archive any jar file(s) generated inside the target directory
        //         archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        //     }
        // }

        stage('Executing jar file') {
            steps {
                // Clean and build the Maven project, fail build on error
                bat 'java -cp target/simple-java-maven-project-1.0-SNAPSHOT.jar com.example.App'  // -B for batch mode (better Jenkins logs)
            }
        }
    }

    post {
        success {
            echo 'Build and archive completed successfully!'
        }
        failure {
            echo 'Build failed! Check console output for errors.'
        }
    }
}