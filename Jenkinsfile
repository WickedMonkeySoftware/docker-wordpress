node {
  // Mark the code build 'stage'....
  stage 'Build'

  docker.withRegistry('http://10.0.0.4') {
    // Build the docker container
    def img = docker.build "10.0.0.4/wordpress:${env.BRANCH_NAME}"

    stage 'push'

    img.push()
   }
}