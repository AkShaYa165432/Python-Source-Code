node {
    def app

 

    stage('Clone Repository') {


 

        checkout scm
    }

 

    stage('Build Image') {

       app = docker.build("akshaya23/pythoncode")
       
    }

    stage('Push Image') {

        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
    stage('Docker Run') {
	def dockerImage = docker.image('akshaya23/pythoncode:'+"${env.BUILD_NUMBER}")
            sh 'docker rm -f app'
            dockerImage.run('-d -p 8081:8080 --name app')  
	}

 

   
}
