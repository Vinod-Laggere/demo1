pipeline {
	agent any
	tools {
        maven 'm395' 
	jfrog 'jfrog-cli'	
    }
        environment {
            CI=true
            ARTIFACTORY_ACCESS_TOKEN = credentials('jfrog-token')
        }
        stages{
              stage ('Build) {
                    steps{
                        sh './mvn clean install'
                    }
              }
              stage ('Upload to artifactory') {
                    steps {
                          sh 'jfrog rt upload --url http://20.219.35.125:8082/artifactory/ --access-token $(ARTIFACTORY_ACCESS_TOKEN) target/demo1-0.0.1-SNAPSHOT.jar my-repo/'
                    }
              }
        }
}
