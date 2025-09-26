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
            bat "echo always"
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
                //bat "chcp 65001\n vrunner init-dev --v8version 8.3.23.1912 --dt C:\\1c_new_agent\\template\\1Cv8.dt --db-user Teacher --src C:\\repo\\jenkins_cicd\\src --ibconnection /FC:\\repo\\jenkins_cicd\\build\\ib"
                bat "chcp 65001\n vrunner init-dev"
            }
        }       
    stage {
        stage("Syntax check"){
            bat "chcp 65001\n vrunner syntax-check"
        }
    } 
    }
}