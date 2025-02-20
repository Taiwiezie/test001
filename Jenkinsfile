pipeline {
    
   agent {
   label 'AnsibleEDA'
   }
   
   options {
   timestamps()
   buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '2', numToKeepStr: '2')
   }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout poll: false, 
                scm: scmGit(branches: [[name: 'feature/testing001']], 
                extensions: [], 
                userRemoteConfigs: [[credentialsId: 'Jenkins-Github', url: 'git@github.com:Taiwiezie/test001.git']])
            }
        }
        stage('clean') {
            steps {
                // cleanWs cleanWhenFailure: false, disableDeferredWipeout: true, notFailBuild: true
                cleanWs()
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
    }
}

