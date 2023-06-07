pipeline {
   
   agent {
     label "built-in"
   }

    stages {
	   stage ("compile stage") {
          steps {
		     sh "mvn compile"  
		  
	   
	   }
     }
       stage ("test stage") {
	       steps { 
              sh "mvn test"
		}
	  }
       stage ("package stage"){
	      steps {
              sh "mvn package"
		}		  
      }	  
	  stage ("build stage"){
	     steps {
		    sh "docker build -t pratibha_tomcat ."
		 }
	  }
	    stage ("deploy to staging"){
		   steps {
		      sh "docker run -d  -it -v /root/.jenkins/workspace/tomcat-docker-pipeline/target/:/usr/local/tomcat/webapps/ -p 8081:8080 --name testtomcat pratibha_tomcat"
		   
		   }
		}
   }
}

