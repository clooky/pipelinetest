pipeline {
    agent any
    stages {
        stage ('GIT Checkout') {
            steps {
                git 'https://github.com/clooky/pipelinetest.git'
            }
        }
        stage ('Build') {
            steps {
            sh label: 'Build', script: 'build.sh'          
            }
        }
        stage ('Test') {
            steps {
            echo "Tested sucessfully";            
            }
        }
        stage ('Deploy') {
            steps {
            echo "Deployed sucessfully";            
            }
        }
    }
    post {
        always {
            echo "This will always run";
        }
        success {
            echo "This will run only if successful";
        }
        failure {
            echo "This will run only if failed";
        }
        unstable {
            echo "This will run only if the run was marked unstable";
        }
        changed {
            echo "This will run only if the state of the pipeline has changed";
            echo "For example: if the pipeline was previously failing but is now successful";
        }
    }
}
