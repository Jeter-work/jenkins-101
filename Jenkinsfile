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
                date
                cd myapp
                python3 -m venv build_env
                source build_env/bin/activate
                /home/jenkins/workspace/my_first_build_pipeline/myapp/build_env/bin/python3 -m pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                source build_env/bin/activate
                python3 hello.py
                python3 hello.py --name=Scott
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