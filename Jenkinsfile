pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Arunasri-0096/task7-mail.git', branch: 'main'
                echo 'Code checkout successful'
                script {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Checkout Success",
                         body: "Code pulled from GitHub successfully"
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Build Stage Successful'
                script {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Build Success",
                         body: "Build stage completed successfully"
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Test Stage Successful'
                script {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Test Success",
                         body: "Test stage completed successfully"
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t task7 .'
                script {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Docker Build Success",
                         body: "Docker image built successfully"
                }
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Docker Push Successful (add docker login if needed)'
                script {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Docker Push Success",
                         body: "Docker image pushed successfully"
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8990:8080 task7'
                script {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Deployment Success",
                         body: "Application deployed successfully"
                }
            }
        }
    }

    post {
        failure {
            script {
                mail to: 'srividyapsn2014@gmail.com',
                     subject: "Pipeline Failed",
                     body: "Something failed in pipeline"
            }
        }
    }
}
