pipeline{
   agent any
   stages {
     stage ("Install required packages"){
	 steps
	 { 
	   sh "sudo yum install httpd git docker -y"
	   sh "sudo systemctl start httpd"
	   sh "sudo systemctl start docker"
	   }
	                                     }
										 
	   stage ("Copy index.html from main"){
	   steps {
	     sh " rm -rf /mnt/assign1 || true"
         sh " mkdir -p /mnt/assign1"
		 sh "git clone -b main https://github.com/nikitap485/httpd-repo.git /mnt/assign1"
              }
	     }
	   stage ("Run docker main"){
	    steps{
		 sh "docker rm -f cont1 || true"
         sh "docker run -d --name cont1 -p 8081:80 httpd"
		 sh "docker cp /mnt/assign1/index.html cont1:/usr/local/apache2/htdocs/index.html"
         sh "docker exec cont1 chmod 777 /usr/local/apache2/htdocs/index.html"
             }
		}
		
		
		}
	 
   
   }
