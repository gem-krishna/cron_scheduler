// def cronExpression = '* */2 * * *'
properties([
  parameters([
    string(name: 'ENV', defaultValue: 'User', description: 'Enter your name')
    booleanParam(name: 'FLAG', defaultValue: false, description: 'A boolean parameter')
  ]),
  pipelineTriggers([
    parameterizedCron('''
        */2 * * * * %ENV=dev;FLAG=true
        */3 * * * * %FLAG=true
    ''')
  ])
])

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