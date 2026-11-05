pipeline {
    agent {
        node {
            label 'docker-agent-python'
        }
    }

    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage('Check Python') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                sh '''
                    cd myapp

                    # Create virtual environment
                    python3 -m venv .venv

                    # Install dependencies inside venv
                    .venv/bin/python -m pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh '''
                    cd myapp

                    # Run Python using virtual environment
                    .venv/bin/python hello.py
                    .venv/bin/python hello.py --name=Brad
                '''
            }
        }

        stage('Deliver') {
            steps {
                echo 'Deliver...'
                sh '''
                    echo "doing delivery stuff.."
                '''
            }
        }
    }
}
