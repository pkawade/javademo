pipeline {
    agent { label 'pramod-agent' }
    parameters { 
        string(name: 'BRANCH_NAME', defaultValue: 'master', description: 'Branch to build') 
    }
    stages {
        stage('Checkout the Code') {
            steps {
                // Debugging: print the branch name
                echo "Checking out branch: ${params.BRANCH_NAME}"
                
                // Use the parameter in the checkout step
                checkout scmGit(branches: [[name: "*/${params.BRANCH_NAME}"]], extensions: [], userRemoteConfigs: [[url: 'https://github.com/pkawade/javademo.git']])
            }
        }
        stage('Build') {
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
