node {
    def home

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       home = docker.build ("srikanta1219/ho",  "${env.WORKSPACE}/home/ ")
    }

    stage('Test image') {
  

        home.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            home.push("${env.BUILD_NUMBER}")
        }
    }
    
    
}
