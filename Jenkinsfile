pipeline {
  agent any

  environment {
    PATH="/opt/maven/bin:$PATH"
  }

  stages {
     // build start
     stage("build"){
       steps {
         sh "mvn clean package"
       }
     }
     // build end

     stage("SonarQube Analysis"){
       environment {
         scannerHome= tool "sandy-sonar-scanner"
       }

       steps {
         echo "sonar server start"
         withSonarQubeEnv("sandy-sonar-server"){
            sh "${scannerHome}/bin/sonar-scanner"
         }
         echo "sonar server end"
       }

     }


  }

}
