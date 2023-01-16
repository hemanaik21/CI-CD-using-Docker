pipeline {
    agent any
	
	  tools
    {
       maven "MAVEN"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/hemanaik21/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp hemanaik/docrepo21:latest'

                //sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) 
          sh  'docker push hemanaik/docrepo21:tagname'

        //  sh  'docker push nikhilnidhi/samplewebapp:$BUILD_NUMBER' 
        }
                  
          }
  
     
      //stage('Run Docker container on Jenkins Agent') {
             
            //steps 
			{
                //sh "docker run -d -p 8003:8080 nikhilnidhi/samplewebapp"
 
            //}
        //}
 //stage('Run Docker container on remote hosts') {
             
            //steps {
               // sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 8003:8080 nikhilnidhi/samplewebapp"
 
            //}
        //}
    }
	}
}
    
