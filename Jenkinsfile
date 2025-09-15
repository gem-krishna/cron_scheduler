// def cronExpression = '* */2 * * *'
// properties([
//   parameters([
//     string(name: 'ENV', defaultValue: 'User', description: 'Enter your name'),
//     booleanParam(name: 'FLAG', defaultValue: false, description: 'A boolean parameter')
//   ]),
//   pipelineTriggers([
//     parameterizedCron('''
//         */2 * * * * %ENV=dev;FLAG=true
//         */3 * * * * %FLAG=true
//     ''')
//   ])
// ])

pipeline {
    agent any

    parameters {
        string(name: 'ENV', defaultValue: 'User', description: 'Enter your name')
        booleanParam(name: 'FLAG', defaultValue: false, description: 'A boolean parameter')
    }

    stages {
        stage('Hello'){
            steps{
                echo 'Hello, World!'
                echo "ENV: ${params.ENV}"
                echo "FLAG: ${params.FLAG}"
            }
        }
        stage('Test'){
            when {
                expression { return params.FLAG == true && params.ENV == 'dev'}
            }
            steps {
                echo 'FLAG is true, executing Test stage.'
            }
        }
    }
    post{
        success{
            echo 'Passed'
        }
        failure{
            echo 'Failed'
        }
    }
}