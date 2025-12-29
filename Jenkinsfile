pipeline {
     agent { label 'agent-1' }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/fsdmubashar/springboot-java-poject.git'
            }
        }
        
        stage('Lint HTML') {
            steps {
                sh 'npx htmlhint *.html'
            }
        }
        
        stage('Lint CSS') {
            steps {
                sh 'npx stylelint "*.css"'
            }
        }
        
        stage('Lint JavaScript') {
            steps {
                sh 'npx eslint *.js'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application...
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded! The app is ready for deployment.'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for errors.'
        }
    }
}

