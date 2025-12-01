pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'   // use the Maven installation configured in Jenkins
        jdk 'JAVA_HOME'      // use the JDK configured in Jenkins
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                // Works on Windows Jenkins and Linux Jenkins
                sh 'mvn -version || mvn -v'
                sh 'mvn clean install'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "BUILD SUCCESSFUL ✔"
        }
        failure {
            echo "BUILD FAILED ✘"
        }
    }
}
