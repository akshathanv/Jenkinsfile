node {
  stage 'Checkout'
  git url: 'https://github.com/akshathanv/Jpetstore_maven.git'   
  // Clean any locally modified files and ensure we are actually on origin/master
  // as a failed release could leave the local workspace ahead of origin/master
  sh "git clean -f && git reset --hard origin/master"
  def mvnHome = tool 'M3'
  stage 'Build'
  sh "${mvnHome}/bin/mvn clean install"
  
  stage 'Run SonarQube analysis'
  sh "${mvnHome}/bin/mvn sonar:sonar -Dsonar.host.url=http://16.181.237.15:9000/"
}
