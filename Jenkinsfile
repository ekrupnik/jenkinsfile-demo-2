echo "Hello from jenkinsfile-demo-2 repo"


node {
   // Mark the code checkout 'stage'....
   stage 'Checkout'

   // Get some code from a GitHub repository
   git url: 'https://github.com/ekrupnik/jenkinsfile-demo-2.git'

   stage 'Static Analysis: Tailor'
   sh "rake tailor"

   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.
  // def mvnHome =

   // Mark the code build 'stage'....
   stage 'Build'
   sh "rake build"
   // Run the maven build
  // sh "${mvnHome}/bin/mvn clean install"


stage 'Post Build Actions'
step([$class: 'GitHubCommitStatusSetter', errorHandlers: [[$class: 'ShallowAnyErrorHandler']], statusResultSource: [$class: 'ConditionalStatusResultSource', results: []]])

stage 'Deploy to DEV'
echo "this is where the DEV deploy logic would go. Still a TODO."
}