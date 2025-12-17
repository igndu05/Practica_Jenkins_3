pipeline {
    agent any

    tools {
        nodejs 'node'
    }

    stages {
        stage('Verify npm and node') {
            steps {
                sh 'node -v'
            }
        }

        stage('Install') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Verify dependencies') {
            steps {
                echo 'Verifying installed dependencies...'
                // Muestra las dependencias de primer nivel
                sh 'npm list --depth=0'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'npm run build'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }
    }
}
