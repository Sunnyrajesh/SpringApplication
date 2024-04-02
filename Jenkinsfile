pipeline {
    agent any 
    tools {
        maven 'MAVEN_HOME'
	    dockerTool 'docker'
    }
    stages {
        stage('Build Maven') {
            steps {
                // Build the Maven project
                bat 'mvn clean install'
            }
        }
        stage('Build docker image') {
            steps {
                script {
                    // Build Docker image with a tag
                    bat 'docker build -t pannamrajesh/spring-application .'
                }
            }
        }
        stage('Run container') {
            steps {
                script {
                    // Run Docker container
                    // pannamrajesh is a repoistory/imagename
                    bat 'docker run -d -p 8080:8080 pannamrajesh/spring-application'
                }
            }
        }
    }
}
