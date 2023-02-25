pipeline {
   agent any
   environment {
     DEPLOY_ONLY = 'false'
   } 
   stages {
     stage('init') {
       when {
//          allOf {
//            expression { branch 'main' || branch 'develop' }
//            expression { env.DEPLOY_ONLY == 'true' }
//          }
          allOf {
             anyOf {
                branch 'main'
                branch 'develop'
             }
             expression { env.DEPLOY_ONLY == 'true' } 
          }
       }
       steps {
         script {
            echo "INIT STEP"
         }
       }
     }
   }
  
}
