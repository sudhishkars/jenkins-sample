pipeline {
   agent any

   parameters {
      string (name: 'DEPLOY_ONLY', defaultValue: 'false', description: 'Skip all stages and go to deploy')
   }

   stages {

     stage ('build') {
        when {
           allOf {              
             anyOf {
               branch 'develop'
               branch 'release-*'
             }
             expression { params.DEPLOY_ONLY == 'false' } 
           }
        }
        steps {
           script {
              echo "******* BUILD STEP ********"
           }
        }
     }

     stage ('test') {
        when {
           allOf {              
             anyOf {
               branch 'develop'
               branch 'release-*'
             }
             expression { params.DEPLOY_ONLY == 'false' } 
           }
        }
        steps {
           script {
              echo "******* TEST STEP ********"
           }
        }
     }   

     stage('Dev deploy') {
       when {
          anyOf {
             branch 'develop'
             expression { params.DEPLOY_ONLY == 'true' }
          }
       }
       steps {
         script {
            echo "******* DEV DEPLOY STEP ********"
         }
       }
     }

     stage('QA deploy') {
       when {
          anyOf {
             branch 'release-*'
             expression { params.DEPLOY_ONLY == 'true' }
          }
       }
       steps {
         script {
            echo "******* QA DEPLOY STEP ********"
         }
       }
     }

     stage('STAGE deploy') {
       when {
          anyOf {
             expression { params.DEPLOY_ONLY == 'true' }
          }
       }
       steps {
         script {
            echo "******* STAGE DEPLOY STEP ********"
         }
       }
     }

     stage('PROD deploy') {
       when {
          anyOf {
             expression { params.DEPLOY_ONLY == 'true' }
          }
       }
       steps {
         script {
            echo "******* PROD DEPLOY STEP ********"
         }
       }
     }                



   }   
  
}
