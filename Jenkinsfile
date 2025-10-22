pipeline {
    agent any

    stages {
        stage('Restore dependences') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run unit and integretion tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
