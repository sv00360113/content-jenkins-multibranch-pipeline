pipeline {
  agent any
//		environment {
//		 ANT_HOME = /usr/share/ant
//		BUILD_VERSION = 1
 		
//}
     stages {
stage (checkout) {
    steps { 
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '1ce37f6d-067a-4bec-a066-934f48d56fc0', url: 'https://github.com/sv00360113/content-jenkins-multibranch-pipeline.git']]])
}


}
		stage ('build') {
				steps {
withAnt {
    // some block
//       		bat "${ANT_HOME}\\bin\\ant -f build.xml"
			sh "ant -f build.xml"
         		step([$class: 'ArtifactArchiver', artifacts: 'Test.html', fingerprint: true])


}
}
}
		stage ("deploy")  {
			steps {
				sh 'cp -r dist/ /tmp/'
}
}
}
}
