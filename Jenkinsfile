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
                  sh '''
                  echo "Stopping old container (if any)..."
                  docker stop springboot-app || true
                  docker rm springboot-app || true

                  echo "Building Docker image..."
                  docker build -t springboot-app:latest .

                  echo "Starting new container..."
                  docker run -d -p 80:80 --name springboot-app springboot-app:latest
                  '''
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


