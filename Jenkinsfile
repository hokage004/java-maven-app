pipeline {
    agent any

    parameters {
        choice(
            name: 'VERSION',
            choices: ['1.1', '1.2', '1.3'],
            description: 'Select application version'
        )

        booleanParam(
            name: 'executeTests',
            defaultValue: true,
            description: 'Execute tests?'
        )
    }

    stages {
        stage('build') {
            steps {
                echo 'building the application...'
            }
        }

        stage('test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                echo 'testing the application...'
            }
        }

        stage('deploy') {
            steps {
                echo 'deploying the application...'
                echo "deploying version ${params.VERSION}"
            }
        }
    }
}
