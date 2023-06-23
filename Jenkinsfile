node {
    def app

 

    stage('Clone Repository') {


 

        checkout scm
    }

 

    stage('Build Image') {

       app = docker.build("akshaya23/pythoncode")
       sh 'docker run -d --name=img2 -p 3000:3000 akshaya23/pythoncode:latest'
    }

 

  

 

    stage('Push Image') {

        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
        }
    }

 

   
}
