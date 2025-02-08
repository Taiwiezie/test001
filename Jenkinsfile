pipeline {
    
   agent {
   label 'aee-eda-inbound'
   }
   
   options {
   timestamps()
   buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '2', numToKeepStr: '2')
   }

    stages {
        stage('clean') {
            steps {
                cleanWs cleanWhenFailure: false, disableDeferredWipeout: true, notFailBuild: true
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Show version') {
            steps {
                sh 'ansible --version'
                sh 'ansible-playbook --version'
                sh 'ansible-rulebook --version'
            }
        }
        stage('Ping test') {
            steps {
                sh 'ansible dev -i /opt/Rules/inventory -l vm05 -m ping'
            }
        }
    }
}

