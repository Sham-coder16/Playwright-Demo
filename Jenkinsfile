pipeline {

    agent any

    triggers {
        cron('0 0 * * *')
        githubPush()
    }

    stages {

        stage('Quick Check - Smoke Tests') {

            steps {
                echo "GitHub Push Build"
                echo "Running Smoke Tests..."

                // Replace with your Playwright command later
                bat 'echo npx playwright test --grep @smoke'
            }
        }

        stage('Full Regression') {

            when {
                triggeredBy 'TimerTrigger'
            }

            steps {

                echo "Nightly Scheduled Build"

                echo "Running Full Regression..."

                // Replace with your Playwright command later
                bat 'echo npx playwright test'

            }

        }

    }

}
