pipeline
{
    agent {
        label '1c_new'
    }

    environment {
        envString = 'true'
    }

    post {
        always {
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure']]
            junit stdioRetention: 'ALL', testResults: 'out/syntax-check/junit/*.xml'
        }

        failure {
            bat "echo failure"
        }

        success {
           bat "echo succes"
        }
    }
    stages {
        stage("Build test base") {
            steps {
                bat "chcp 65001\n vrunner init-dev"
                
            }
        }
        stage("Syntax sheck") {
            steps {
              bat "chcp 65001\n vrunner syntax-check"
            }
        }  
      
    }     
}