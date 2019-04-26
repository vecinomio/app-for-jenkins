pipeline {
  agent node1
  stages {
    stage('build') {
      steps {
        echo 'building app.....'
      }
    }
    stage('build package') {
      steps {
        echo 'buiding package.....'
      }
    }

    stage('SSH transfer') {
      script {
        sshPublisher(
          continueOnError: false, failOnError: true,
          publishers: [
            sshPublisherDesc(
              configName: "Prod",
              verbose: true,
              transfers: [
                sshTransfer(
                  sourceFiles: "*",
                  removePrefix: "",
                  remoteDirectory: "",
                  execCommand: "sudo systemctl restart httpd"
                )
              ])
          ])
       }
    }
  }
}
