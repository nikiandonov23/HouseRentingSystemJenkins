pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Изтегля кода от хранилището, конфигурирано в секцията SCM
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                echo 'Restoring NuGet packages...'
                // Възстановява зависимостите, необходими за проекта
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Компилира проекта, за да провери за грешки при компилация
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                echo 'Executing tests...'
                // Стартира автоматичните тестове
                bat 'dotnet test --no-build'
            }
        }
    }
}