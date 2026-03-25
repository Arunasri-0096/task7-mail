pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "arunasri0096/mail"
    }

    stages {

        stage('Build') {
            steps {
                echo 'Build Stage Successful'
            }
            post {
                success {
                    mail to: 'srividyapsn2014@gmail.com',
                    subject: 'Build Success',
                    body: 'Build completed successfully'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Test Stage Successful'
            }
            post {
                success {
                    mail to: 'srividyapsn2014@gmail.com',
                    subject: 'Test Success',
                    body: 'Tests passed successfully'
                }
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:latest")
                }
            }
            post {
                success {
                    mail to: 'srividyapsn2014@gmail.com',
                    subject: 'Docker Build Success',
                    body: 'Docker image built'
                }
            }
        }

        stage('Docker Push') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-id') {
                        docker.image("${DOCKER_IMAGE}:latest").push()
                    }
                }
            }
            post {
                success {
                    mail to: 'srividyapsn2014@gmail.com',
                    subject: 'Docker Push Success',
                    body: 'Image pushed to DockerHub'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
            }
            post {
                success {
                    mail to: 'srividyapsn2014@gmail.com',
                    subject: 'Deployment Success',
                    body: 'App deployed to Kubernetes'
                }
            }
        }
    }
}
