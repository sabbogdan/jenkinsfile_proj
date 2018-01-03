
node("Slave 1") {
   def mvnHome
   stage('Preparation') { 

      git 'https://github.com/spring-guides/gs-maven.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'Maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
//      junit '**/target/surefire-reports/TEST-*.xml'
 archiveArtifacts 'target/*.jar'
 }
}
