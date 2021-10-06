pipeline {
    agent none
    stages {
        stage('Prepare') {
            agent {
                docker {
                    image 'ubuntu:20.04'
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'ubuntu:20.04'
                }
            }
            steps {
                sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
        stage('Deploy') {
            agent {
                docker {
                    image 'ubuntu:20.04'
                }
            }
            steps {
                sh '/root/.pyenv/shims/pyinstaller -F sources/add2vals.py'
            }
            post {
                success {
                    archiveArtifacts 'dist/add2vals'
                }
            }
        }
    }
}
