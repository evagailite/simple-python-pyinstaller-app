pipeline {
    agent none
    stages 
        stage('Prepare') {
            agent {
                docker {
                    image 'ubuntu:20.04'
                }
            }
            steps {
                echo 'Running Prepare Stage'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'ubuntu:20.04'
                }
            }
            steps {
                echo 'Running Test Stage'
            }
        }
        stage('Deploy') {
            agent {
                docker {
                    image 'ubuntu:20.04'
                }
            }
            steps {
                echo 'Running Deploy Stage'
            }
        }
    }
}
