pipeline
{
    agent {
        label '1c'
    }

    environment {
        envString = 'true'
    }

    post {
        always {
            //bat "echo hello"
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
                //bat "chcp 1251\n echo Первый этап сборки"
                //bat "chcp 65001\n vrunner init-dev --dt C:\\jenkins\\template\\dev.dt --db-user Teacher --src C:\\repo\\sonar_repo\\src"
                bat "vrunner init-dev --v8version 8.3.23.1912  --ibconnection /FC:\\repo\\jenkins_repo\\build\\ib --dt C:\\jenkins\\template\\dev.dt --db-user Teacher --src C:\\repo\\jenkins_repo\\src"
            }
        }       
        stage("Syntax check"){
            steps{
                bat "chcp 65001\n vrunner syntax-check"
            }
        } 
    }
}