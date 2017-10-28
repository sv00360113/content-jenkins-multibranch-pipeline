pipeline {
	agent any
		stages {
			stage ('build') {
				steps {
				sh 'javac -d . src/*.java'
				sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
				sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
					}
				}
			post {
				success {
			archiveArtifacts artifact: 'rectangle.jar', fingerprint: true
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
				echo "stashing local changes"
				sh 'git stash'
				echo "checking out development"
				sh 'git checkout developement' 
				sh 'git pull origin development"
				echo "checking out master"
				sh 'git checkout master'
				echo "merging development into master"
				sh 'git merge development'
				echo "git push to master"
				sh 'git push origin master'
				}
		}
	}
}

