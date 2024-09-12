pipeline {
    agent any
    
    stages {
        stage('Clean and Package-Dev'){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/dev';
                }
            }
            steps{
            	withMaven(maven: 'MAVEN_HOME', mavenSettingsFilePath: 'settings.xml') {
                        echo "Start Clean and Package"
                        sh """mvn clean package"""
                        echo "End Clean and Package"
                }
            }
        }
        stage('Clean and Package-Sit'){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/sit';
                }
            }
            steps{
                withMaven(maven: 'MAVEN_HOME', mavenSettingsFilePath: 'settings.xml') {
                        echo "Start Clean and Package"
                        sh """mvn clean package"""
                        echo "End Clean and Package"
                }
            }
        }
        stage('Clean and Package-Uat'){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/uat';
                }
            }
            steps{
                withMaven(maven: 'MAVEN_HOME', mavenSettingsFilePath: 'settings.xml') {
                        echo "Start Clean and Package"
                        sh """mvn clean package"""
                        echo "End Clean and Package"
                }
            }
        }
    }
}