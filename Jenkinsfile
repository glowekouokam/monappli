pipeline {
	agent any
	stages {
		stage ( '----clean---') {
			steps {
				sh "mvn clean"
			}
		}
		stage('---test--') {
			steps {
				sh "mvn test"
			}
		}
		stage ('----package---') {
			steps {
				sh "mvn package"
			}
		}
                stage ('----script---') {
			steps {
				sh label: '', script: 'echo LOOOOOOOOOOOOOOOWWWWWWWWWWWWWWWWWWWWWWWWWEEEEEEEEEEEEEEEE'
			}
		}
		stage('-----deploy----') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
				withMaven(mavenSettingsConfig: 'mvn-setting-xml') {
					sh "mvn deploy"
				}
            }
        }
	}
}
