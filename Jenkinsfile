pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-username/my-web-app.git' // Replace with your repository URL
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building...'
                // Add any build steps if needed
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add any test steps if needed
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    def server = 'your-ec2-public-ip' // Replace with your EC2 instance public IP
                    def user = 'ec2-user' // Adjust if needed
                    def key = '/path/to/your/key.pem' // Path to your SSH key

                    sh """
                        scp -i ${key} -o StrictHostKeyChecking=no index.html ${user}@${server}:/var/www/html/
                        ssh -i ${key} -o StrictHostKeyChecking=no ${user}@${server} 'sudo systemctl restart nginx'
                    """
                }
            }
        }
    }
}
