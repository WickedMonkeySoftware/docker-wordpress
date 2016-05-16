node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Get some code from a GitHub repository
   git url: 'https://github.com/jglick/simple-maven-project-with-tests.git'

   // Mark the code build 'stage'....
   stage 'Build'

   // Build the docker container
   def img = docker.build '10.0.0.4/wordpress:${env.BUILD_TAG}'

   img.push()
}