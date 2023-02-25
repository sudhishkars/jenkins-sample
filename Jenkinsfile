pipeline {
   agent any
   envrionment {
     DEPLOY_ONLY = 'true'
   } 
   stages {
     stage('init') {
       when {
         allOf {
           expression { branch 'main' || branch 'develop' }
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
