pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    sh 'git clone https://github.com/shivadarshan-devadiga/PES1UG22CS560_Jenkins repo'
                    sh 'cd repo && touch program.cpp && echo "#include<iostream>\nusing namespace std;\nint main() { cout << \\"Hello, World!\\" << endl; return 0; }" > program.cpp'
                    sh 'cd repo && git add program.cpp && git commit -m "Added new working .cpp file" && git push origin main'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'mkdir -p build'
                    sh 'g++ repo/program.cpp -o build/PES1UG22CS560-1'
                    echo 'Build Stage Successful'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './build/PES1UG22CS560-1'
                    echo 'Test Stage Successful'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'cp build/PES1UG22CS560-1 /usr/local/bin/'
                    echo 'Deployment Successful'
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
