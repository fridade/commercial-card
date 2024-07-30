pipeline {
    agent any
    


    stages {
        stage('clean env') {
            steps {
                sh '''
            docker system prune -fa || true
                '''
            }
        }
        
        stage('compile') {
            steps {
               sh 'mvn compile'
            }
        }

        



        stage('Test') {
            steps {
                sh "mvn test  -DskipTests=true"
            }
        }


        stage('File System Scan') {
            steps {
                sh "trivy fs --format table -o trivy-fs-report.html ."
            }
        }

    //    stage('SonarQube analysis') {
    //        agent {
    //            docker {
    //              image 'sonarsource/sonar-scanner-cli:4.8.0'
    //            }
    //           }
    //           environment {
    //    CI = 'true'
    //    scannerHome='/opt/sonar-scanner'
    //    }
    //        steps{
    //            withSonarQubeEnv('sonar') {
    //                sh "${scannerHome}/bin/sonar-scanner"
    //            }
    //    }
    stage('Build') {
            steps {
               sh "mvn package -DskipTests=true "
            }
    
    }
    stage('Build-images') {
            steps {
                sh '''
              docker build -t  fridade/comm-card:jenkins-$BUILD_NUMBER .
                '''
            }

    }

    stage('Push-ui') {
          
            steps {
               sh 'fridade/comm-card:jenkins-$BUILD_NUMBER'
            }
    }




       
        





   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   }































}
