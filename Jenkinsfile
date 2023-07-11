podTemplate {
  node(POD_LABEL) {

    stage('Initialize'){
        def dockerHome = tool 'DockerTool'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }

    stage("test docker client") {
      sh "docker -v"
    }

    stage('Build Wordpress Image')  {
        sh "docker build -t nnvu187/wordpress-custom ."
    }

    stage('Push Wordpress Image') {
        sh "docker push nnvu187/wordpress-custom"
    }

    stage("Clean up") {
        sh "docker rmi nnvu187/wordpress-custom:$BUILD_NUMBER"    
    }
  }
}