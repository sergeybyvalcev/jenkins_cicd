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
                bat "chcp 65001\n vrunner init-dev"
                
            }
        }   
      
    }     
}