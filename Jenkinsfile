pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Ashu6605/my-demo.git'
            }
        }

        stage('Deploy Static Website') {
            steps {
                sh '''
                sudo systemctl start httpd
                sudo systemctl enable httpd

                sudo rm -rf /var/www/html/*
                sudo cp -r * /var/www/html/

                sudo chown -R apache:apache /var/www/html
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Static website deployed successfully'
        }
        failure {
            echo '❌ Deployment failed'
        }
    }
}
