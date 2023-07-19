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
		stage ("docker build-23Q2") { 
			steps { 
				sh '''
				rm -rf *
				git clone https://github.com/pritam-jagtap/multibranch-project.git -b 23Q2
				docker pull httpd
    				
				chmod -R 777 /tmp/multibranch-project/index.html
				docker run -itdp 90:80 --name 23Q2 httpd
				docker cp /tmp/multibranch-project/index.html 23Q2:/usr/local/apache2/htdocs
  				'''
				}
				}
                    }
           }
