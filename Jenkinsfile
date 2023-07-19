 pipeline {
	agent {
		label {
		label "built-in"
		customWorkspace "/tmp"
		}
	}
	stages {
		stage ("install docker"){
		steps {
			sh ''' 
			yum install docker -y
			systemctl  start docker
			systemctl enable docker
			'''
  			
			}
				}
		stage ("docker build-23Q3") { 
			steps { 
				sh '''
				rm -rf *
				git clone https://github.com/pritam-jagtap/multibranch-project.git -b 23Q3
				docker pull httpd
    				docker stop 23Q3
    				docker rm 23Q3
				docker run -itdp 8081:80 --name 23Q3 httpd
				docker cp /tmp/multibranch-project/index.html 23Q3:/usr/local/apache2/htdocs
  				'''
				}
				}
		
		}

	}
