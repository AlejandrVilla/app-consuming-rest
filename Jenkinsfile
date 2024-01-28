pipeline{
	agent any
	stages{
		stage("version"){
			steps{
				echo "version..."
				sh "java -version"
			}
		}
		stage("build"){
			steps{
				echo "building..."
                dir("consuming-rest"){
                    sh "pwd"
                    sh './gradlew build'
                }
			}
		}
        stage("deploy"){
            steps{
                echo "deploying..."
				dir("quoter"){
					sh "pwd"
					sh "ls -al"
					// sh 'mvn clean install'
					// sh "rm -r target"
					sh "./mvnw spring-boot:run &"
                    // sh "cat log.txt"
                    // sh "rm log.txt"
				}
                dir("consuming-rest"){
                    sh "java -jar build/libs/consuming-rest-0.0.1-SNAPSHOT.jar &"
                    // sh "cat log.txt"
                    // sh "rm log2.txt"
                }
            }
        }
	}
}