node {
    checkout scm
    def dockerfile = 'Dockerfile'
    def customImage = docker.build("my-image:${env.BUILD_ID}", "-f ${dockerfile} .") 
}