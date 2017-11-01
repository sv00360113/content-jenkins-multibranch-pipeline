pipeline {
  agent any
       environment {
              antVersion = 'Ant1.9.4'
                  }
withEnv( ["ANT_HOME=${tool antVersion}"] ) {
    sh '$ANT_HOME/bin/ant target1 target2'
}
     stages {
stage (checkout) {
    steps { 
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '1ce37f6d-067a-4bec-a066-934f48d56fc0', url: 'https://github.com/sv00360113/content-jenkins-multibranch-pipeline.git']]])
}


}
		stage ('build') {
			steps {
			withEnv( ["ANT_HOME=${tool antVersion}"] ) {
    sh '$ANT_HOME/bin/ant war'
}
}
}
}
}
