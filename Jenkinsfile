pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'Maven v3.9.5', globalMavenSettingsConfig: 'MavenSettings') {
                    script {
                        version = sh script: 'mvn help:evaluate -Dexpression=project.version -q -DforceStdout',
                            returnStdout: true
                        currentBuild.description = "Version: ${version}"
                    }
                    sh './mvnw verify'
                }
            }
        }
        stage('Test') {
            steps {
                echo "Start Tests"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy to Test-Environment"
            }
        }
    }
}
