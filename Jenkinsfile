currentBuild.displayName = "Artifactory - #"+currentBuild.number
pipeline {
  agent any
   stages {
      stage("CheckOut-SCM"){
          steps{
                      cleanWs()
                        checkout([$class: 'GitSCM', 
                                  branches: [[name: '*/master']], 
                                  doGenerateSubmoduleConfigurations: false,
                                  extensions: [], 
                                  submoduleCfg: [], 
                                  userRemoteConfigs: [[credentialsId: 'Jenkins_credentials',
                                  url: 'https://github.com/admin-2013/pune-barclays.git']]])             
                 }
                          }
       stage("Build"){
           steps{
                    sh label: '', script: 'mvn package'
                   }
             }
             
             stage("archiveArtifacts"){
           steps{
                   archiveArtifacts '**/*.war'
                   }
             }

   }
}
