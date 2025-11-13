pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/Dhusyanth2005/jenkinstest.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📦 Installing Node modules...'
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                bat 'npm test'
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building project...'
                bat 'npm run build'
            }
        }

        stage('Archive Build Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: '**/*', fingerprint: true
            }
        }

        stage('Deploy (Optional)') {
            steps {
                echo 'Deploying application...'
                bat 'npm start'
            }
        }
    }

    post {
        success {
            echo 'Build and Deploy Successful!'
        }
        failure {
            echo 'Build Failed! Check console logs.'
        }
    }
}
