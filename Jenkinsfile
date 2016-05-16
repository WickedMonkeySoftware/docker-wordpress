node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Get some code from a GitHub repository
   checkout scm

   // Mark the code build 'stage'....
   stage 'Build'

   // Build the docker container
   def img = docker.build '10.0.0.4/wordpress:${env.BRANCH_NAME}'

   img.push()
}