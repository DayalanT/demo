pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK11"
    }

    stages {
        stage('Fetch code') {
            steps {
                git branch: 'main', url: 'https://github.com/hkhcoder/vprofile-project.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn install -DskipTests'
            }
            post {
                success {
                    echo 'Archiving artifacts now.'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage('Unit test') {
            steps {
                sh 'mvn test'
            }
        }


    }
}
