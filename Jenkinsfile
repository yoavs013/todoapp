node {
    
	

    def newApp
    def registry = 'yoavs013/todo'
    def registryCredential = 'dockerhub'
	
	stage('Git') {
		git 'https://github.com/yoavs013/todoapp.git'
	}
	stage('Build') {
		sh 'npm install'
	}
	stage('Test') {
		sh 'npm test'
	}
	stage('Building image') {
        docker.withRegistry( 'https://' + registry, registryCredential ) {
		    def buildName = registry + ":$BUILD_NUMBER"
			newApp = docker.build buildName
			newApp.push()
        }
	}

}
