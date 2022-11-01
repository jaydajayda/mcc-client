node {
    
    stage ("Checkout React Client"){
        git branch: 'main', url: 'https://github.com/jaydajayda/mcc-client.git'
    }
    
    stage ("Install dependencies") {
        sh 'npm install'
    }
    
    stage ("Containerize the app-docker build") {
        sh 'docker build --rm -t mccclient:v1.0 .'
    }
    
    stage ("Inspect the docker image"){
        sh "docker images mccclient:v1.0"
        sh "docker inspect mccclient:v1.0"
    }
    
    stage ("Run Docker container instance"){
        sh "docker run -d --rm --name mccclient -p 3000:3000 mccclient:v1.0"
     }
    
    stage("User Acceptance Test") {
	
	  def response = input message: 'Is this build good to go?',
	   parameters: [choice(choices: 'Yes\nNo', 
	   description: '', name: 'Pass')]
	
	  if(response=="Yes") {
	    stage('Deploy to Kubernetes cluster') {
	      sh "kubectl create deployment mccclient --image=mccclient:v1.0"
	      sh "kubectl expose deployment mccclient --type=LoadBalancer --port=80"
	    }
	  }
    }

    stage("Production Deployment View"){
        sh "kubectl get all"
    }
}