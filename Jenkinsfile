node {
    
	

    def newApp
	def registry = 'https://registry-1.docker.io/v2/'
	def imagename = "yoavs013/todo"
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
		    def buildName = registry +":'$BRANCH_NAME'_'$BUILD_NUMBER'"
			newApp = docker.build buildName
			newApp.push()
        }
	}

}
