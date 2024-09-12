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
                    withCredentials([string(credentialsId: 'secureKeyPreProd', variable: 'secureKeyPreProd')]) {
                        echo "Start Clean and Package"
                        sh """mvn clean package -Denv=DEV -Dford.secureKey=${secureKeyPreProd}"""
                        echo "End Clean and Package"
                    }
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
                    withCredentials([string(credentialsId: 'secureKeyPreProd', variable: 'secureKeyPreProd')]) {
                        echo "Start Clean and Package"
                        sh """mvn clean package -Denv=SIT -Dford.secureKey=${secureKeyPreProd}"""
                        echo "End Clean and Package"
                    }
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
                    withCredentials([string(credentialsId: 'secureKeyPreProd', variable: 'secureKeyPreProd')]) {
                        echo "Start Clean and Package"
                        sh """mvn clean package -Denv=UAT -Dford.secureKey=${secureKeyPreProd}"""
                        echo "End Clean and Package"
                    }
                }
            }
        }
        stage('Clean and Package-Prod'){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main';
                }
            }
            steps{
                withMaven(maven: 'MAVEN_HOME', mavenSettingsFilePath: 'settings.xml') {
                    withCredentials([string(credentialsId: 'secureKeyProd', variable: 'secureKeyProd')]) {
                        echo "Start Clean and Package"
                        sh """mvn clean package -Denv=PROD -Dford.secureKey=${secureKeyProd}"""
                        echo "End Clean and Package"
                    }
                }
            }
        }
    }
}