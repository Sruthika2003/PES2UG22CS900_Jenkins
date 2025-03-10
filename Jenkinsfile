pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'g++ -o PES2UG22CS900-1 test.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS900-1'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'git config --global user.name "T B Sruthika"'
                    sh 'git config --global user.email "sruthikatb@gmail.com"'
                    sh 'git checkout -B main origin/main'  // Ensures correct branch checkout
                    sh 'git add -A'
                    sh 'git commit -m "Added test.cpp file" || echo "No changes to commit"'
                    sh 'git push origin main'  // Push changes back to GitHub
                }
            }
        }


        stage('Post Actions') {
            steps {
                echo "Pipeline completed successfully"
            }
        }
    }

    post {
        success {
            echo "Build and deployment successful!"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}
