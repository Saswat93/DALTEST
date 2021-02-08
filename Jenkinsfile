pipeline
{
    agent {label 'master'}
    stages {
        stage ("====STAGE A====="){
            steps {
        git 'https://github.com/Saswat93/simple-java-maven-app.git'
        echo "Hi Saswat"
            }
    }
        stage ( "=====STAGE B===="){
            steps {
            echo "Hello====================================================="
            }
        }
    }
}