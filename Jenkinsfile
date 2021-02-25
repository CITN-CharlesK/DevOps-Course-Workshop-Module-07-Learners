pipeline {
    agent any

    stages {
        stage('Builds the .Net') {
            steps {
                sh 'dotnet build'
                echo 'Building .Net..'
            }
        }
        stage('Runs the C# tests.') {
            steps {
                sh 'dotnet test'
                echo 'Running C# Tests...'
            }
        }
        stage('Install node packages.') {
            steps {
                dir("./DotnetTemplate.Web") {
                    sh 'npm install'
                }
                echo 'Installing node packages...'
            }
        }
        stage('build node packages') {
            steps {
                dir("./DotnetTemplate.Web") {
                    sh 'npm run build'
                }
                echo 'Building node packages...'
            }
        }
        stage('Runs the C# tests.') {
            steps {
                dir("./DotnetTemplate.Web.Tests") {
                    sh 'dotnet test'
                }
                echo 'Running .Net Tests...'
            }
        }
        stage('typescript tests.') {
            steps {
                dir("./DotnetTemplate.Web/Scripts/spec") {
                    sh 'npm t'
                }
                echo 'Running typescript tests...'
            }
        }
        stage('Runs the C# tests.') {
            steps {
                dir("./DotnetTemplate.Web") {
                    sh 'npm run lint'
                }
                echo 'Running linting on the typescript code...'
            }
        }
    }
}
