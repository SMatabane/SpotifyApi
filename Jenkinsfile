pipeline {
    agent any
    environment {
        MAVEN_HOME = 'C:\\apache-maven-3.9.6'
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    
                    try {
                        git branch: 'main', credentialsId: '9ad2d862-1e64-42d5-8d6d-92c018b724e8', url: 'https://github.com/SMatabane/SpotifyApi.git'
                    } catch (Exception e) {
                        error "Checkout failed: ${e.message}"
                    }
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    dir('SpotifyApi')
                    try {
                        bat "${MAVEN_HOME}/bin/mvn clean compile -DskipTests"
                    } catch (Exception e) {
                        error "Build stage failed: ${e.message}"
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    dir('SpotifyApi')
                    try {
                        bat "${MAVEN_HOME}/bin/mvn test -DsuiteXmlFile=testng.xml"
                    } catch (Exception e) {
                        error "Test stage failed: ${e.message}"
                    }
                }
            }
        }
        stage('Allure Report') {
            steps {
                script {
                    dir('SpotifyApi')
                    try {
                        allure includeProperties: false, results: [[path: 'target/allure-results']]
                    } catch (Exception e) {
                        echo "Allure report generation failed: ${e.message}"
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed. Running post-actions.'
            archiveArtifacts artifacts: '**/target/allure-results/**', allowEmptyArchive: true
            junit 'target/surefire-reports/*.xml'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Sending notification...'
            // Add notification steps here, e.g., email or Slack integration
             mail to: 'mankgethwa286@gmail.com',
         subject: "Build failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
         body: "Build failed in ${env.JOB_NAME} (${env.BUILD_NUMBER}). Check Jenkins logs for details."
        }
    }
}
