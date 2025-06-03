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
            allure includeProperties: false, jdk: '', results: [[path: 'out/syntax-check/allure'], [path: 'out/smoke/allure/']]
            junit allowEmptyResults: true , testResults: 'out/smoke/junit/*.xml'
        }

        // failure {
        //     bat "echo failure"
        // }

        // success {
        //     bat "echo succes"
        // }

    }

    stages {
        stage("Build test base") {
            steps {                
                //bat "chcp 1251\n echo Первый этап сборки"
                // bat "echo Без кодировки"
                // bat "chcp 1251\n echo Первый этап 1251"
                // bat "chcp 65001\n echo Первый этап 65001"
                //bat "chcp 65001\n vrunner init-dev --dt C:\\jenkins\\template\\dev.dt --db-user Teacher --src C:\\repo\\sonar_repo\\src"
                // bat "chcp 65001\n vrunner init-dev --v8version 8.3.23.1912  --ibconnection /FC:\\repo\\jenkins_repo\\build\\ib --dt C:\\jenkins\\template\\dev.dt --db-user Teacher --src C:\\repo\\jenkins_repo\\src"
                bat "chcp 65001\n vrunner init-dev --dt C:\\jenkins\\template\\dev.dt --src C:\\repo\\jenkins_repo\\src"
            }
        }       
        stage("Syntax check") {
            steps {
                // bat "chcp 65001\n echo Первый этап сборки"
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
        stage("Vanessa") {
            steps {
                script {
                    try {
                        bat "chcp 65001\n vrunner vanessa"
                    }
                    catch(Exception Exc) {
                        currentBuild.result = 'UNSTABLE'
                    }
                }                
            }
        } 
    }
}