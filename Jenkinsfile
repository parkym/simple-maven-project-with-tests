node('master'){
  checkout scm
  def mvnHome
 stage('preparation'){
    git 'https://github.com/jglick/simple-maven-project-with-tests.git'
    mvnHome = tool 'M3'
 }
  stage('Build'){
    //bat 'mvn -Dmaven.test.failure.ignore clean package'
    bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
  }
  state('results'){
    junit '**/target/surefire-reports/TEST-*.xml'
    archiveArtifacts 'target/*.jar'
  }
}
