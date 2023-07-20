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
                   withCredentials([sshUserPrivateKey(credentialsId: '913e5d57-48cc-4309-90aa-0854ed98de32', keyFileVariable: 'sshKeyFile')]) {
     
                       bat '''
                        git status
                        git checkout main
                        git pull -f -p origin main
                        git reset --hard HEAD
                        git status
                        git config --local user.email "farrukh1@gmail.com"
                        git config --local user.name "farrukh"
                        echo "modifying... file 1" > file1.txt                        
                        git status
                        
                        git commit file1.txt -m "modifying file1" 
                        git push origin main
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
