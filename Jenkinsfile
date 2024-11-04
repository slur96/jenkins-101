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
        stage('Build') {
            steps {
                echo "Building.."
                dir('myapp') {
                    // Set up virtual environment
                    sh 'python3 -m venv venv'
                    // Activate the virtual machine and install dependencies
                    sh '. venv/bin/activate && pip install -r requirements.txt'
                }
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                dir('myapp') {
                    // Activate the virtual environment before running tests
                    sh '. venv/bin/activate && python3 hello.py'
                }
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
