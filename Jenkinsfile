pipeline {
  agent any
     stages {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '1ce37f6d-067a-4bec-a066-934f48d56fc0', url: 'https://github.com/sv00360113/content-jenkins-multibranch-pipeline.git']]])
}
}

