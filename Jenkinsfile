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
            bat "echo hello"
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
                bat "chcp 1251\n echo Первый этап сборки"
                //bat "chcp 65001\n vrunner init-dev --dt C:\\jenkins\\template\\dev.dt --db-user Teacher --src C:\\repo\\sonar_repo\\src"
            }
        }       
         
    }
}