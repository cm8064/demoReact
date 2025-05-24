pipeline {
    agent any

tools{
nodejs 'Node_24'
}

    stages {
        stage('Checkout') {
            steps {
                echo 'step 1 - Checkout de rama'
                git branch: 'main', url: 'https://github.com/cm8064/demoReact.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Step 2 - Compilación'
                sh 'npm install'
                sh 'cd react2'
                sh 'cd ucp-app'
                sh 'npm run build'
            }
        }
        stage('Unit test') {
            steps {
                echo 'Step 3 - Pruebas unitarias'
            }
            post{
                always{
                    archiveArtifacts artifacts: 'test-outputs.txt',
                    allowEmptyArchive: true
                }
            }
        }
    }
        post{
            success{
                echo "Pipeline finalizado con éxito"
            }
            failure{
                echo 'Pipeline con errores'
            }
        }
    }
