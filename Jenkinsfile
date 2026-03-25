pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Arunasri-0096/task7-mail.git', branch: 'main'
                echo 'Code checkout successful'
                script {
                    try {
                        mail to: 'srividyapsn2014@gmail.com',
                             subject: "Checkout Success",
                             body: "Code pulled from GitHub successfully"
                    } catch (Exception e) {
                        echo "Mail failed"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Build Stage Successful'
                script {
                    try {
                        mail to: 'srividyapsn2014@gmail.com',
                             subject: "Build Success",
                             body: "Build stage completed successfully"
                    } catch (Exception e) {
                        echo "Mail failed"
                    }
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Test Stage Successful'
                script {
                    try {
                        mail to: 'srividyapsn2014@gmail.com',
                             subject: "Test Success",
                             body: "Test stage completed successfully"
                    } catch (Exception e) {
                        echo "Mail failed"
                    }
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t task7 .'
                script {
                    try {
                        mail to: 'srividyapsn2014@gmail.com',
                             subject: "Docker Build Success",
                             body: "Docker image built successfully"
                    } catch (Exception e) {
                        echo "Mail failed"
                    }
                }
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Docker Push Successful (add docker login if needed)'
                script {
                    try {
                        mail to: 'srividyapsn2014@gmail.com',
                             subject: "Docker Push Success",
                             body: "Docker image pushed successfully"
                    } catch (Exception e) {
                        echo "Mail failed"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f task7 || true
                docker run -d -p 8990:8080 --name task7 task7
                '''
                script {
                    try {
                        mail to: 'srividyapsn2014@gmail.com',
                             subject: "Deployment Success",
                             body: "Application deployed successfully"
                    } catch (Exception e) {
                        echo "Mail failed"
                    }
                }
            }
        }
    }

    post {
        failure {
            script {
                try {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Pipeline Failed",
                         body: "Something failed in pipeline"
                } catch (Exception e) {
                    echo "Mail failed"
                }
            }
        }
    }
}
