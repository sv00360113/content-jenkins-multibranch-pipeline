pipeline { 
	agent any
		environment {
			MAJOR_VERSION = 1
				}
		stages {
			stage ('build') {
				steps {
					 sh 'javac -d . src/*.java'         
					 sh 'echo Main-Class: Rectangulator > MANIFEST.MF'         
					 sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class' 
					}
			post {
				success {
				archiveArtifacts artifacts: 'rectangle.jar', fingerprint:true
				}
			}
	}
			stage ('run') {
				steps {
					sh 'java -jar rectangle.jar 7 9' 
					}
					}
			stage ('promote development to master') {
				when {
					branch 'development'
					}
				steps {
					echo "stashing local change"
					sh 'git stash'
					echo "checking out development"
					sh 'git checkout development'
					sh 'git pull origin development'
					echo "checking out master"
					sh 'git checkout master'
					sh 'git merge development'
					sh 'git push origin master'
					}
				}
			stage ('Tagging the release') {
				when {
					branch 'master'
					}
				steps {
					sh 'git tag rectangle-${env.MAJOR_VERSION}.${BUILD_NUMBER}'
					sh 'git push rectangle-${env.MAJOR_VERSION}.${BUILD_NUMBER}'
 					}
					}	
				}
}	
