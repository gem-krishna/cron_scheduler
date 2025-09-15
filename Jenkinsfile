pipeline {
    agent any

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