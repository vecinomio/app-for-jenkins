pipeline {
  agent { label 'node1' }
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
      steps {
        sshPublisher(
          continueOnError: false, failOnError: true,
          publishers: [
            sshPublisherDesc(
              configName: "Prod",
              verbose: true,
              transfers: [
                sshTransfer(
                  sourceFiles: "*.html",
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
