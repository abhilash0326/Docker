pipeline{
	agent{
		label {
						node 'slave-1'
						customWorkspace '/'
						}
	}
		stages{
				
				stage('installing docker'){
									
									steps{
										dir ('/'){
										sh "sudo yum install docker -y"
										sh "sudo systemctl start docker"
										sh "sudo sleep 5"
										}
									}
									steps{
										sh "docker run --name container1 -itdp httpd 80:80 bash"
										sh "docker run --name container2 -itdp httpd 80:90 bash"
										sh "docker run --name container3 -itdp httpd 80:8080 bash"
									
									}
				
											
									
				}
				stage('cloning git'){
									
									steps{
											sh "mkdir /mt/data"
											sh "chmod -R 777 /mnt/data"
										dir ('/mnt/data'){
										sh "rm -rf *"
										sh "git clone -b 22Q1 https://github.com/abhilash0326/Docker.git 22Q1"
										sh "git clone -b 22Q2 https://github.com/abhilash0326/Docker.git 22Q2"
										sh "git clone -b 22Q3 https://github.com/abhilash0326/Docker.git 22Q3"
											}
									}
				}
				stage('deployment of index.html'){
									
									steps{
										sh "docker cp /mnt/data/22Q1/index.html container1:/usr/local/apache2/htdocs/"
										sh "docker cp /mnt/data/22Q2/index.html container2:/usr/local/apache2/htdocs/"
										sh "docker cp /mnt/data/22Q3/index.html container3:/usr/local/apache2/htdocs/"
									
									}
											
									
				}
		}
}
