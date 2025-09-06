pipeline {
    agent { 
        node {
            label 'docker-agent-py'
        }
    }
    triggers {
      pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                    python3 -m venv venv
                    source venv/bin/activate
                    cd myapp
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                    cd myapp
                    python3 hello.py
                    python3 hello.py --name=Aaron
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo "Deliver...."
            }
        }
    }
}
