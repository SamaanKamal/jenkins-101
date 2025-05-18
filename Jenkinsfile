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
                sh '''
                # Navigate to the application directory
                cd myapp
                
                # Install virtualenv (if it's not already installed)
                python3 -m pip install --user virtualenv
                
                # Create a virtual environment
                python3 -m venv venv
                
                # Activate the virtual environment
                source venv/bin/activate
                
                # Install the dependencies in the virtual environment
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                
                # Activate the virtual environment
                source venv/bin/activate
                
                # Run the tests
                python3 hello.py
                python3 hello.py --name=Brad
                '''
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
