pipeline {
    agent any

    environment {
        registry = "013920193168.dkr.ecr.us-east-1.amazonaws.com/ecr_ecs"
    }

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Git checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/pillakarthik4/Microservice-Deploy-using-Helm.git']]])
            }
        }

        stage('Build Jar') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def mvn = tool 'Maven3'
                    withSonarQubeEnv {
                        sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=tomcat-deploy1"
                    }
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build registry
                    dockerImage.tag("${BUILD_NUMBER}")
                }
            }
        }

        stage('Push to ECR') {
            steps {
                script {
                    sh "aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 013920193168.dkr.ecr.us-east-1.amazonaws.com"
                    sh "docker push 013920193168.dkr.ecr.us-east-1.amazonaws.com/ecr_ecs:${BUILD_NUMBER}"
                }
            }
        }

        stage('Helm deploy') {
            steps {
                script {
                    sh "helm upgrade first --install mychart --namespace helm-deployment --set image.tag=${BUILD_NUMBER}"
                }
            }
        }
    }
}

