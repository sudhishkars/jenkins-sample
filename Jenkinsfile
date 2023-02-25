pipeline {
   agent any
   parameters {
      string (name: 'DO_DEPLOY', defaultValue: 'false', description: 'Skip all stages and go to deploy')
   }
   stages {
     stage ('build') {
        when {
           anyOf {
              branch 'develop'
              branch 'test'
           }
        }
        steps {
           script {
              echo "Build"
           }
        }
     }    
     stage('deploy') {
       when {
          allOf {
             anyOf {
                branch 'main'
                branch 'develop'
             }
             expression { params.DO_DEPLOY == 'true' } 
          }
       }
       steps {
         script {
            echo "Deploy"
         }
       }
     }
   }
  
}
