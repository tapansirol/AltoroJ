node{
  stage ('cloning the repository'){
      git 'https://github.com/tapansirol/AltoroJ.git'
  }
	
  //stage('SonarQube analysis') {
    // requires SonarQube Scanner 2.8+
    //def scannerHome = tool 'sonar-new';
    //withSonarQubeEnv('My SonarQube Server') {
     // sh "${scannerHome}/bin/sonar-scanner"
    //}
  //}
  stage('Gradle Build') {
       //def gradleHome = tool name : 'mygradle', type 'gradle',
        //sh "${gradleHome}/bin/gradle clean build"
        def path = tool name: 'gradle-4.7', type: 'gradle'
        sh "${path}/bin/gradle build"
   }
   
   stage('SonarQube analysis') {
    withSonarQubeEnv('sonar-server') {
        sh "./gradlew clean sonarqube"
    }
  }
}
