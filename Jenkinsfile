pipeline {
    agent any

    environment {
        RECIPIENT_EMAIL = 'snehagopalappa@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build the code using Maven.'
                echo 'Tool: Maven'
                // Example command: sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Run Unit and Integration Tests using JUnit and TestNG.'
                echo 'Tools: JUnit, TestNG'
                // Example command: sh 'mvn test'
            }
            post {
                success {
                    mail to: "${env.RECIPIENT_EMAIL}",
                         subject: "Jenkins Pipeline: Unit and Integration Tests Passed",
                         body: "The Unit and Integration Tests stage has completed successfully. Check the Jenkins console output for details."
                }
                failure {
                    mail to: "${env.RECIPIENT_EMAIL}",
                         subject: "Jenkins Pipeline: Unit and Integration Tests Failed",
                         body: "The Unit and Integration Tests stage has failed. Check the Jenkins console output for details."
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Perform code analysis using SonarQube.'
                echo 'Tool: SonarQube'
                // Example command: sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Perform security scan using OWASP Dependency-Check.'
                echo 'Tool: OWASP Dependency-Check'
                // Example command: sh 'dependency-check.sh --project my-project --scan .'
            }
            post {
                success {
                    mail to: "${env.RECIPIENT_EMAIL}",
                         subject: "Jenkins Pipeline: Security Scan Passed",
                         body: "The Security Scan stage has completed successfully. Check the Jenkins console output for details."
                }
                failure {
                    mail to: "${env.RECIPIENT_EMAIL}",
                         subject: "Jenkins Pipeline: Security Scan Failed",
                         body: "The Security Scan stage has failed. Check the Jenkins console output for details."
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy the application to a staging server (AWS EC2).'
                echo 'Tool: AWS CLI'
                // Example command: sh 'aws deploy push --application-name my-app --s3-location s3://my-bucket/my-app.zip'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Run Integration Tests on the staging environment.'
                echo 'Tools: JUnit, TestNG'
                // Example command: sh 'mvn verify'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy the application to the production server (AWS EC2).'
                echo 'Tool: AWS CLI'
                // Example command: sh 'aws deploy push --application-name my-app --s3-location s3://my-bucket/my-app.zip'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
