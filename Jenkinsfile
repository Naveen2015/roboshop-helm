pipeline {
    agent any
    parameters {
        string(name: 'component', defaultValue: '', description: 'App Component Name')
    }
    stages {
        stage('Clone App Repo') {
            steps {
                dir('APP') {
                    git branch: 'main', url: "https://github.com/Naveen2015/${params.component}.git"
                }
            }
        }
        stage('Helm Deploy') {
            steps {
                dir('APP') {
                    sh 'helm upgrade -i ${component} . -f APP/values.yaml'
                }
            }
        }
    }
}