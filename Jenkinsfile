pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh './mvnw clean install'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh './mvnw test'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/**.exec'
                jacocoReport(
                    executionData: 'target/**.exec',
                    classPattern: 'target/classes',
                    sourcePattern: 'src/main/java'
                )
            }
        }
    }
    triggers {
        cron('H/3 * * * 1')
    }
}
