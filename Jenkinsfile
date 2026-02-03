pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Ashu6605/my-demo.git'
            }
        }

        stage('Install Apache (httpd)') {
            steps {
                sh '''
                sudo yum install -y httpd
                sudo systemctl start httpd
                sudo systemctl enable httpd
                '''
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                sudo cp index.html /var/www/html/
                sudo chmod 644 /var/www/html/index.html
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment successful! Website is live."
        }
        failure {
            echo "❌ Deployment failed."
        }
    }
}
