node{

   def tomcatWeb = 'D:\\AKSHAY\\JenkinsWar\\src\\main\\webapp'
   def tomcatBin = 'D:\\AKSHAY\\JenkinsWar\\src\\main\\webapp'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/akshay1552/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         bat "${tomcatBin}\\index.jsp"
   }
}
