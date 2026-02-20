@Library('jenkins-shared') _

pipeline {
    agent any
    environment {
        DOCKER_REO = "piyushaughad/jenkins-shared-mlops-project"

    }
    stages {
        stage('Checkout') {
            steps {
                gitCheckout("https://github.com/piyushaughad/MLOPS-Project-Code.git","*/main","github-token")

            }
        }

        stage('Build & Push Image') {
            steps {
                dockerBuildAndPush("DOCKER_REO","dockerhub-token")
                
            }
        }

        stage('Install Kubectl') {
            steps {
               installKubectl()
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                k8sDeploy("kubeconfig","k8s")
                
            }
        }
    }
}
