@Library("nbshared-library") _
def myCheckoutFunction(branch, subdirectory, URL){
        checkout([$class: 'GitSCM',
                         branches: [[name: branch]],
                         doGenerateSubmoduleConfigurations: false,
                         extensions: [[$class: 'RelativeTargetDirectory',
                         relativeTargetDir: subdirectory]],
                         submoduleCfg: [],
                         userRemoteConfigs: [[url: URL]]
                         ])
                    }
pipeline{
    agent any
    stages{
        stage("create subdirectory"){
            steps{
                script{
                        myCheckoutFunction("main", "multibranch", "https://github.com/nbacadlabs/multibranch.git")
                        myCheckoutFunction("main", "csharptutorials", "https://github.com/nbacadlabs/c-sharp-tutorials.git")
                        // myCheckoutFunction("main", "terraformintegration", "https://github.com/nbacadlabs/terraform-integration.git")
                }
     
                }
            }
        stage("List current directory"){
            steps{
                  sh 'ls $PWD'
                }
            }
        stage("Call helloWorld"){
            steps{
                  helloWorldSimple()
                }
            }
        }
    }