pipeline {
    agent { label 'docker' }

    triggers {
        githubPush()
    }

    parameters {
        string(name: 'GIT_REPO_URL', defaultValue: 'git@github.com:valdemar414/realworld-angular-dockerized.git', description: 'Git Repository URL')
        string(name: 'DOCKER_IMAGE_STG', defaultValue: '0686519782/onb-stg-frontend', description: 'Docker Image Name for Staging')
        string(name: 'DOCKER_IMAGE_PROD', defaultValue: '0686519782/onb-prod-frontend', description: 'Docker Image Name for Production')
        string(name: 'DOCKER_IMAGE_MAJOR_TAG', defaultValue: '0.1.', description: '')
    }

    environment {
        DOCKERHUB_CREDENTIALS = 'onb-prod-dockerhubCreds'
        GIT_CREDENTIALS_ID = 'onb-prod-gitSSHcred'
        DOCKERFILE_STG = 'Dockerfile.stg'
        DOCKERFILE_PROD = 'Dockerfile.prod'
    }

    stages {
        stage('Clone repository') {
            steps {
                git credentialsId: env.GIT_CREDENTIALS_ID, url: params.GIT_REPO_URL
            }
        }

    //     stage('Build Docker Image STG') {
    //         steps {
    //             script {
    //                 def customImageSTG = docker.build("${params.DOCKER_IMAGE_STG}:${params.DOCKER_IMAGE_MAJOR_TAG}${env.BUILD_ID}", "-f ${env.DOCKERFILE_STG} .")
    //                 customImageSTG.tag("latest", false)

                    
    //             }
    //         }
    //     }

    //     stage('Push Docker Image STG') {
    //         steps {
    //             script {
    //                 docker.withRegistry('https://registry.hub.docker.com', env.DOCKERHUB_CREDENTIALS) {
    //                     docker.image("${params.DOCKER_IMAGE_STG}:${params.DOCKER_IMAGE_MAJOR_TAG}${env.BUILD_ID}").push()
    //                     docker.image("${params.DOCKER_IMAGE_STG}:latest").push()
    //                 }
    //             }
    //         }
    //     }
            
    //     stage('Build Docker Image PROD') {
    //         steps {
    //             script {
    //                 def customImageSTG = docker.build("${params.DOCKER_IMAGE_PROD}:${params.DOCKER_IMAGE_MAJOR_TAG}${env.BUILD_ID}", "-f ${env.DOCKERFILE_PROD} .")
    //                 customImageSTG.tag("latest", false)
    //             }
    //         }
    //     }

    //     stage('Push Docker Image PROD') {
    //         steps {
    //             script {
    //                 docker.withRegistry('https://registry.hub.docker.com', env.DOCKERHUB_CREDENTIALS) {
    //                     docker.image("${params.DOCKER_IMAGE_PROD}:${params.DOCKER_IMAGE_MAJOR_TAG}${env.BUILD_ID}").push()
    //                     docker.image("${params.DOCKER_IMAGE_PROD}:latest").push()
    //                 }
    //             }
    //         }
    //     }
    // }

    // post {
    //     always {
    //         cleanWs()
    //     }
    // }
}
