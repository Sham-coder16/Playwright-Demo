pipeline {

    agent any

    parameters {

        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'staging', 'production'],
            description: 'Select the environment'
        )

        choice(
            name: 'BROWSER',
            choices: ['chromium', 'firefox'],
            description: 'Select browser'
        )

        booleanParam(
            name: 'DRY_RUN',
            defaultValue: false,
            description: 'If true, only print commands'
        )
    }

    stages {

        stage('Display Parameters') {
            steps {
                echo "Environment : ${params.ENVIRONMENT}"
                echo "Browser      : ${params.BROWSER}"
                echo "Dry Run      : ${params.DRY_RUN}"
            }
        }

        stage('Run Tests') {

            steps {

                script {

                    if (params.DRY_RUN) {

                        echo "Dry Run Enabled"

                        echo "Command:"
                        echo "npx playwright test --project=${params.BROWSER}"

                    } else {

                        echo "Executing Tests..."

                        bat "echo Running tests on ${params.ENVIRONMENT} using ${params.BROWSER}"

                    }

                }

            }

        }

    }

}
