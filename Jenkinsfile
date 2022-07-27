
node('built-in') 
{
   stage('ContionousDownload') 
       {
               git branch: 'main', url: 'https://github.com/sumanthintime/Jenkins.git'
	           }
		       stage('ContionousBuild') 
		           {
			           sh 'mvn package'
				       }
				           stage('ContionousDeploy') 
					       {
					               deploy adapters: [tomcat9(credentialsId: 'b9307fa6-8638-4164-98d5-7ab83bc62634', path: '', url: 'http://172.31.81.177:8080')], contextPath: 'testapp', war: '**/*.war'
						           }
							        stage('ContionousTesting') 
								    {
								            git branch: 'main', url: 'https://github.com/sumanthintime/FunctionalTesting.git'
									    sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
									        }
										    stage('ContionousDelivery') 
										        {
											        input message: 'Need Approval from DM! to deploy in UAT', submitter: 'mounika'
												        deploy adapters: [tomcat9(credentialsId: 'b9307fa6-8638-4164-98d5-7ab83bc62634', path: '', url: 'http://172.31.80.15:8080')], contextPath: 'prodapp', war: '**/*.war'
													    }
													    }
