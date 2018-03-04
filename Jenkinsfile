node {
	stage('preparation') {
	    checkout scm
	    def dockerfile = 'Dockerfile'
	    def customImage = docker.build("my-image:${env.BUILD_ID}", "-f ${dockerfile} .")
	}
	stage('stop old container') {
		sh 'docker ps -f name=laks-nginx -q | xargs --no-run-if-empty docker container stop'
		sh 'docker container ls -a -fname=laks-nginx -q | xargs -r docker container rm'
	}
	stage('copy deployment file') {
		sh 'cp index.html /opt/html/'
	}
	stage('docker-run') {
		def dockernginx = docker.image("my-image:${env.BUILD_ID}").run("--name laks-nginx --volume /usr/share/nginx/html:/opt/html --publish 80:80")
	}
}
