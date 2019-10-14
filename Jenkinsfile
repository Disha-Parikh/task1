pipeline {
  agent any
  stages {
    stage('build') {
      steps {
             sh '''
                sudo apt-get install python3-pip
                sudo apt-get -y install python-virtualenv
                sudo apt-get install screen -y
                virtualenv flask1
                source flask1/bin/activate
                nohup python /var/lib/jenkins/workspace/flask/routes.py &
                '''
            }
        }
        stage('test'){
                steps{
                sh '''
                sonar-scanner \
  -Dsonar.projectKey=jenkins_flask \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=fef5f29d5350a7ca2c597205e53f0ccf9ff226bc
'''
        }
        }
    }
}

