
pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'

                deleteDir()

                git branch: 'main',
                    url: 'https://github.com/it24sakshidubey-netizen/java-webapp-jenkins-cicd.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Java Web Application using Maven...'
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Maven tests...'
                bat 'mvn test'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo 'Deploying WAR file to Apache Tomcat...'

                bat '''
                copy /Y "target\\java-webapp-jenkins-cicd.war" "C:\\apache-tomcat-9.0.120\\webapps\\java-webapp-jenkins-cicd.war"
                '''
            }
        }
    }

    post {
        success {
            echo '========================================'
            echo 'CI/CD PIPELINE COMPLETED SUCCESSFULLY'
            echo '========================================'
        }

        failure {
            echo '========================================'
            echo 'CI/CD PIPELINE FAILED'
            echo '========================================'
        }
    }
}
