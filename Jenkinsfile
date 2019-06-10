node{
  stage ('cloning the repository'){
      git 'https://github.com/tapansirol/AltoroJ.git'
  }
	
  stage('Gradle Build') {
       //def gradleHome = tool name : 'mygradle', type 'gradle',
        //sh "${gradleHome}/bin/gradle clean build"
        def path = tool name: 'gradle-4.7', type: 'gradle'
        sh "${path}/bin/gradle build"
   }
   
   stage('SonarQube analysis') {
    def path = tool name: 'gradle-4.7', type: 'gradle'
    withSonarQubeEnv('sonar-server') {
        sh "${path}/bin/gradle --info -Dsonar.host.url=$SONAR_HOST_URL sonarqube"
    }
  }
}
