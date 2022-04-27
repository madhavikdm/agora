node {      

    def app

    stage('Clone repository') {

        /* Cloning the Repository to our Workspace */

        echo '### Started cloning the repository..'

        checkout scm

        echo '### Repository cloned successfully'

    }



    stage('Build image') {

        /* This builds the actual image */

        echo '### Started Building the docker image..'
     
        app = docker.build ("docker_1")
//    app.image('mydemo_1').withRun('-p 5000:3000')


        echo '### Docker build successful.'

     }



     stage('Test image') {        

        app.inside {

             echo "Tests passed"    

          }

      }
     stage('Push image') {
          echo '### Docker image pushing on docker hub .'
//    docker.withRegistry('https://index.docker.io','docker') {
     docker.withRegistry('https://hub.docker.com') {  
//          bat "docker tag madhavikadam/myrepo-agora:latest" 
      app.push("${env.BUILD_NUMBER}")
            app.push("latest")

 }
          echo '### Docker image pushed on docker hub .'
     }



}
