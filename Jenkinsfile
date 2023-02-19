pipeline{
agent any
    tools{
    maven "Maven"
    }
    
stages
    {
    stage("code checkout"){
        steps{
        bat "echo hello stage"
        }
    }
    stage("code build"){
        steps{
        bat "mvn clean"
        }
    }
    stage("unit test"){
        steps{
           bat "mvn test"}
        }
    stage ("Sonar Analysis")
    {
        steps{
            withSonarQubeEnv("SonarQubeServerDevTestOps")
            {
                //bat "mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar"
                bat "mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar"

            }
        }
    }
    /* stage("Upload to Artifactory"){
            steps{
            rtMavenDeployer(id: 'deployer', 
                            serverId: '123456789@artifactory', 
                            releaseRepo: 'ksdevtestopscdflow',
                            snapshotRepo: 'ksdevtestopscdflow')
                rtMavenRun(pom:'pom.xml',
                          goals: 'clean install',
                          deployerId: 'deployer')
                rtPublishBuildInfo(serverId: '123456789@artifactory')
            }
        }*/
     }
    post{
        //always{//execute all times
       //}
        success{
        bat "echo success"
        }
    }
}
