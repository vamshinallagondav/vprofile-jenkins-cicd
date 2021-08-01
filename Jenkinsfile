pipeline {

  agent any

  tools {
   maven "maven3"
  }

  environment {

    registry = "vamshinalla/jenkins-cicd"
    registryCredential = 'vamshi@96664'

  }
  stages{

     stage('BUILD'){

       steps{

         sh 'mvn clean install -DskipTests'

       }
       post {

       success{
          echo 'now archaving'
          archavingArtifacts artifacts: '**/target/*.war'
       }

       }

       }


     }
     stage('UNIT TEST'){

       steps{

         sh 'mvn test'

       }


     }

     stage('INTEGRATION TEST'){
        steps{

                sh 'mvn verify -DskipUnitTests'
              }

     }
      stage('CODE ANALYSIS WITH CHECKSTYLE'){

        steps{
          sh 'mvn chekstyle:chekstyle'

        }
        post{

          success{

            echo 'Genarated Analysis Result'

          }

        }

      }
       stage('Building image'){
        steps{
         script{

           dockerImage = docker.build registry + ":$BUILD_NUMBER"

         }

        }

       }




  }



