@Library('shared-library') _

pipeline {
    agent any

    stages {

        stage('Branch Info') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Build') {
            when {
                expression { env.BRANCH_NAME.startsWith("feature/") }
            }
            steps {
                echo "Running simple Build for feature branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Full Pipeline (Main)') {
            when {
                branch 'main'
            }
            steps {
                echo "Running full flow for main branch..."
                myFunction("Shamlin")    // <--- shared library call
            }
        }
    }

    post {
        always {
            echo "Completed job for ${env.BRANCH_NAME}"
        }
    }
}
