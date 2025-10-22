pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup .NET SDK') {
            steps {
                bat '''
                    curl -L https://dot.net/v1/dotnet-install.ps1 -o dotnet-install.ps1
                    powershell -ExecutionPolicy Bypass -File dotnet-install.ps1 -Version %DOTNET_VERSION% -InstallDir "%DOTNET_INSTALL_DIR%"
                '''
            }
        }

        stage('Restore') {
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
