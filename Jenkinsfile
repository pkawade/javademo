pipeline {
    agent { label 'pramod-agent' }
    parameters { string defaultValue: 'master', name: 'branch_name' }
    stages{
        stage("checkout the code") {
            steps {
                checkout scmGit(branches: [[name: "*/${params.BRANCH_NAME}"]], extensions: [], userRemoteConfigs: [[url: 'https://github.com/cloud-dev-user/java-war-project.git/']])
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
