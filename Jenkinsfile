pipeline {
    agent any

    stages {
        stage('Create File') {
            steps {
                script {
                    sh '''
                    echo '#include <iostream>' > program.cpp
                    echo 'using namespace std;' >> program.cpp
                    echo 'int main() {' >> program.cpp
                    echo '    cout << "Hello, Jenkins!" << endl;' >> program.cpp
                    echo '    return 0;' >> program.cpp
                    echo '}' >> program.cpp
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'g++ -o YOUR_SRN-1 program.cpp' // Replace YOUR_SRN with your actual SRN
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS900-1' // Run the compiled C++ file
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh '''
                    git config --global user.name "T B SRUTHIKA"
                    git config --global user.email "sruthikatb@gmail.com"
                    git add program.cpp
                    git commit -m "Added new C++ file"
                    git push origin main
                    '''
                }
            }
        }
    }

    post {
        failure {
            echo 'pipeline failed'
        }
    }
}
