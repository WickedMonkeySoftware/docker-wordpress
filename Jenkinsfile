node {
   // Mark the code build 'stage'....
   stage 'Build'

   // Build the docker container
   def img = docker.build "10.0.0.4/wordpress:${env.BRANCH_NAME}"

   img.push()
}