pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                script {
                    sh 'rm -rf repo || true'
                    sh 'git clone https://github.com/shivadarshan-devadiga/PES1UG22CS560_Jenkins repo'
                    sh 'cd repo && touch program.cpp'
                    sh 'cd repo && echo "#include<iostream>\nusing namespace std;\nint main() { cout << \\"Hello, World!\\" << endl; return 0; }" > program.cpp'
                    sh 'cd repo && git config --global user.email "shivadarshan2212@gmail.com"'
                    sh 'cd repo && git config --global user.name "shivadarshan-devadiga"'
                    sh 'cd repo && git add program.cpp'
                    sh 'cd repo && git commit -m "Added new working .cpp file"'
                    }
            }
        }
        stage('Build') {
            steps {
                sh 'g++ repo/program.cpp -o repo/output'
                echo 'Build Stage Successful'
            }
        }
        stage('Test') {
            steps {
                sh './repo/output'
                echo 'Test Stage Successful'
            }
        }
        stage('Deploy') {
    steps {
        script {
            echo 'Starting Deployment...'
            sh '''
            cd repo
            git push https://shivadarshan-devadiga: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@github.com/shivadarshan-devadiga/PES1UG22CS560_Jenkins main
            '''
            echo 'Deployment Successful!'
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
