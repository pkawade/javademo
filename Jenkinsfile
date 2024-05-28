pipeline {
    agent { label 'pramod-agent' }
    stages{
        stage("checkout the code") {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/cloud-dev-user/java-war-project.git/']])
            }
        }
        stage("build") {
            steps {
                sh 'mvn package'   
            }
        }
        
    }
    post {
        always {
            cleanWs()
            echo 'Workspace cleaned!'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
