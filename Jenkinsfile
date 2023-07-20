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

                   withCredentials([usernamePassword(credentialsId: 'github user password', passwordVariable: 'GITPASS', usernameVariable: 'GITUSER')]) {
    // some block
}
     
                       bat '''
                        git checkout main
                        git pull -f -p https://$GITUSER:$GITPASS@github.com/Farrukhw/ansible.learn.git origin main 
                        echo \"modifying... file\" >> file1.txt                        
                        git add .
                        git commit -a -m "modifying file1" 
                        git push https://$GITUSER:$GITPASS@github.com/Farrukhw/ansible.learn.git
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
