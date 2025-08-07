pipeline {
    agent {
        labels 'slave-1'
    }
    tools {
        maven 'maven-3'
        jdk 'jdk-17'
    }
    stages {
        stage('Cleaning the Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Git checkout') {
            steps {
                git 'https://github.com/pj013525/Hotstar-Application.git'
            }
        }
         stage('Compile the code') {
            steps {
                sh 'mvn compile'
            }
        }
         stage('Test the code') {
            steps {
                sh 'mvn test'
            }
        }
         stage('Code Quality Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh'''
                    sonar-scanner/bin/sonar-scanner \
                    -Dsonar.projectName=Hotstar \
                    -Dsonar.projectKey=Hotstar-app\
                    -Dsonar.sources=. \
                    -Dsonar.projectVersion=1.0
                    '''
                }
            }
        }
         stage('package the code') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Push the Artifact to nexus') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'myapp', classifier: '', file: 'target/myapp.war', type: 'war']], credentialsId: 'nexus-creds', groupId: 'in.PJ', nexusUrl: '3.81.77.173:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'Hotstar', version: '8.3.3-SNAPSHOT'
            }
        }
        stage('Deploy in Tomcat') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat-creds', path: '', url: 'http://52.200.202.19:8080/')], contextPath: 'Hotstar-App', war: '**/*.war'
            }
        }
    }
}
