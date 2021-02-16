pipeline{
    agent {label 'master'}
    
    tools {
        maven "M3maven"
    }
    
    stages {
        
        stage ("GIT CHECKOUT"){
            steps {
               git 'https://github.com/jleetutorial/maven-project.git'
              // git 'https://github.com/Saswat93/simple-java-maven-app.git'
                echo "Yohoo!! My clone Completed==================="
            }
        }
        
        stage ("Build Code"){
            steps{
                // sh "mvn clean package"
                   bat "mvn clean package"
            }
        }
        
        stage ("Upload Artifacts"){
            steps{
                script{
            def server = Artifactory.server 'jfrog'        
            def uploadSpec = """{   
            "files": [{
            
            "pattern": "*",
            "target": "DAL-pipeline/",
            "recursive": "false"
        }]
            }"""
            server.upload(uploadSpec)
            
      }
     }
	 }
	 
	 stage ("Publish Junit Report"){
	     steps{
	         junit '**/target/surefire-reports/TEST-*.xml'
	         archiveArtifacts '*'
	     }
	 }
}
}
