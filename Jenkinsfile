pipeline {
    agent any 
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
    stages {
        stage ('GIT Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'AuthorInChangelog']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/clooky/pipelinetest.git']]])
            }
        }
        stage ('Build') {
            steps {
            sh label: 'Build', script: 'bash ./build.sh'  
            echo "${params.Greeting} World!"
            }
        }
        stage ('Test') {
            steps {
            sh label: 'Test', script: 'bash ./test.sh'           
            }
        }
        stage ('Deploy') {
            steps {
            sh label: 'Deploy', script: 'bash ./deploy.sh'   
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
