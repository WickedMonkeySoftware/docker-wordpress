node {
  stage 'checkout'
  checkout scm

  // Mark the code build 'stage'....
  stage 'Build'

  docker.withRegistry('http://10.0.0.4') {
    // Build the docker container
    def img = docker.build "withinboredom/wordpress:${env.BRANCH_NAME}", "src"

    stage 'push'

    img.push()
  }
}