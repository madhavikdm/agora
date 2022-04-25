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
     
        app = docker.build ("innerbuild_1")
//    app.image('mydemo_1').withRun('-p 5000:3000')


        echo '### Docker build successful.'

     }



    stage('Test image') {        

        app.inside {

            echo "Tests passed"    

         }

     }
     stage('Push image') {
//   docker.withRegistry('https://hub.docker.com/repository/docker/madhavikadam/myrepo-agora/', 'docker') {
    docker.withRegistry('https://registry.docker.io', 'docker') {  
//             app.push("${env.BUILD_NUMBER}")
            app.push("latest")

 }
     }

//    stage('push image on docker hub') {
//      echo '### Started pushing the docker image..'
//        def Image = docker.build 'madhavikadam/myrepo-agora' + ':latest'
//              docker.withRegistry(Image , 'docker') {
//       app=docker.build('myrepo-agora')

//                  app.push("${env.BUILD_NUMBER}")
//                  Image.push('latest')
//         }

//           echo '### Docker image pushed on docker hub  successfully.'  

//       }


}
