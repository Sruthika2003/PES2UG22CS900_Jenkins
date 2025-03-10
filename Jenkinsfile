pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Sruthika2003/PES2UG22CS900_Jenkins'
            }
        }

        stage('Build') {
            steps {
                sh '''
                ls -l test.cpp  # Debugging step: Check if test.cpp exists
                g++ -o PES2UG22CS900-1 test.cpp
                ls -l  # Check if PES2UG22CS900-1 was created
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                chmod +x PES2UG22CS900-1  # Ensure it's executable
                ./PES2UG22CS900-1
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                git add test.cpp
                git commit -m "Updated test.cpp"
                git push origin main
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}
