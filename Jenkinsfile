pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build Stage Successful'
            }
        }

        stage('Test') {
            steps {
                echo 'Test Stage Successful'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Docker Build Successful'
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Docker Push Successful'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment Successful'
            }
        }
    }

    post {
        success {
            script {
                try {
                    mail to: 'srividyapsn2014@gmail.com',
                         subject: "Build Success",
                         body: "Pipeline completed successfully"
                } catch (Exception e) {
                    echo "Mail failed"
                }
            }
        }

        failure {
            echo 'Pipeline Failed'
        }
    }
}
