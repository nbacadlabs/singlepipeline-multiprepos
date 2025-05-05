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
                        myCheckoutFunction("master", "multibranch", "https://github.com/nbacadlabs/multibranch.git")
                        myCheckoutFunction("master", "csharptutorials", "https://github.com/nbacadlabs/c-sharp-tutorials.git")
                        myCheckoutFunction("master", "terraformintegration", "https://github.com/nbacadlabs/terraform-integration.git")
                }
                }
            }
        }
    }