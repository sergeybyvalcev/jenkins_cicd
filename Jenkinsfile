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
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure'], [path: 'out/smoke/allure/']]
            junit stdioRetention: 'ALL', testResults: 'out/smoke/junit/*.xml'
            //bat "echo always"
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

        stage("Syntax check") {
            steps {
                bat "chcp 65001\n vrunner syntax-check"
            }            
        }
        stage("Smoke tests") {
            steps {
                script {
                    try {
                        bat "chcp 65001\n vrunner xunit"
                    }
                    catch(Exception Exc) {
                        currentBuild.result = 'UNSTABLE'
                    }
                }                
            }
        }
    }     
}