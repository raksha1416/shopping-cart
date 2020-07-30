pipeline {
    agent any
    stages{
	stage ('checkout') {
	    steps{
		    checkout([$class: 'GitSCM', branches: [[name: '*/']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/pranshulgupta/shopping-cart.git']]])
	}
	}
	    
	stage('Submit Stack') {
            steps {
		    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-key', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {	     
				    sh "aws cloudformation create-stack --stack-name mynewstack4 --template-body file://stack.json --capabilities CAPABILITY_IAM --region us-east-1"
		    }
          }    
  }
}
}
