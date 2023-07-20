// Declarative //
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                //echo 'Building..'
                echo 'We are in ' + pwd()
            
                // When using a GString at least later Jenkins versions could only handle the env.WORKSPACE variant:
                echo "Current workspace is ${env.WORKSPACE}"
            
                // the current Jenkins instances will support the short syntax, too:
                echo "Current workspace is $WORKSPACE"

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                dir ("$WORKSPACE") {
                   bat 'dir'
                   echo 'We are in ' + pwd()
                   withCredentials([sshUserPrivateKey(credentialsId: '913e5d57-48cc-4309-90aa-0854ed98de32', keyFileVariable: '')]) {
     
                       bat '''
                        git status
                        git checkout main
                        git pull -f -p
                        git status
                       '''                    
                    }
                }
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
