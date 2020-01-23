pipeline {

      agent any

      stages {

            stage('GIT') {

                  steps {

                        echo 'Hi, this is Satyam from 3Pillar'

                        echo 'We are Starting the Testing'
                        git 'https://github.com/satyam1998/Jenkins.git'

                  }

            }
            stage('COMPILE_packege') {

                  steps {

                        echo 'COMPILE THE FILE'
                        tool name: 'Local_maven', type: 'maven'
                        sh 'mvn -f java-tomcat-sample/pom.xml package'
                        


                  }

            }

            stage('Build') {

                  steps {

                        echo 'Building Sample Maven Project'
                        archiveArtifacts '**/*.war'

                  }

            }
            stage('Deploy') {

                  steps {

                        echo 'Deploying Sample Maven Project'
                        copyArtifacts filter: '**/*.war', fingerprintArtifacts: true, projectName: 'First-pipeline', selector: workspace()
                        deploy adapters: [tomcat9(credentialsId: 'e146d8f5-fef8-4a23-a417-cd9d82495697', path: '', url: 'http://52.15.132.162:9090/')], contextPath: '/', war: '**/*.war'

                  }

            }


      }

}
