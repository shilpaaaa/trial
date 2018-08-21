pipeline {
    agent any

    stages {
        stage('Validate') {
            steps {
                git 'https://github.com/shilpaaaa/samplejenkins.git'
                 sh 'mvn validate'
                 sh 'cp -pr settings.xml ~/.m2/'
                echo 'Building..'
            }
        }
        stage('Compile') {
            steps {
                git 'https://github.com/shilpaaaa/samplejenkins.git'
                sh 'mvn compile'
                echo 'Compile'
            }
        }
        stage('Test') {
            steps {
                git 'https://github.com/shilpaaaa/samplejenkins.git'
                sh 'mvn test'
                               
                echo 'Testing'
            }
        }
        
        stage('Sonarqube') {
            steps {
                git 'https://github.com/shilpaaaa/samplejenkins.git'
           sh 'mvn sonar:sonar'
                echo 'Testing'
            }
        }
        stage('Package') {
            steps {
                git 'https://github.com/shilpaaaa/samplejenkins.git'
                sh 'mvn package'
                echo 'Packageing'
            }
        }
        stage('Nexus') {
           steps {
               git 'https://github.com/shilpaaaa/samplejenkins.git'
               sh 'mvn deploy'
               echo 'Nexus'
            }
        }
        stage('Deploying') {
            steps {
                git 'https://github.com/shilpaaaa/samplejenkins.git'
                sh 'mvn clean package'
                sh 'mvn tomcat7:redeploy'

                echo 'Deploying'
            }
        }
    }
}
