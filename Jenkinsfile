node {
	stage('preparation') {
	    checkout scm
	    def dockerfile = 'Dockerfile'
	    def customImage = docker.build("my-image:${env.BUILD_ID}", "-f ${dockerfile} .")
	}
	stage('docker-run') {
		def dockernginx = docker.image("my-image:${env.BUILD_ID}").run("--name laks-nginx -volume /var/www/html:/opt/html --publish 80:80")
	}
}
