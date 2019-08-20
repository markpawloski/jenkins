pipeline{
  agent any
  environment{
    def CONNECT_SERVER = "http://myconnectserver.pawloski.net/__api__/v1"
    def CONNECT_API_KEY = "sdfjlkjdflkjsldkjslkdj"
    def CONTENT_NAME = "Test Content Name"
    def CONTENT_TITLE = "Test Content Title"
    def ORIGINAL_GUID = ""
    def DEV_BRANCH = "development"
    def PROD_BRANCH = "master"
    def isProd = "false"
  }
  stages{
    stage("Build Bundle"){
      steps{
        echo "Workspace: ${WORKSPACE}"
      }
    }
    stage("Create Connect Content"){
      steps{
        echo "Create Content"
      }
    }
    stage("Deploy - Development"){
      when{expression{env.BRANCH_NAME == "${DEV_BRANCH}"}}
      steps{
        echo "Development"
      }
    }
    stage("Deploy - Production"){
     when{expression{env.BRANCH_NAME == "${PROD_BRANCH}"}}
      steps{
        echo "Approval for Prod..."
        timeout(time:3,unit:'MINUTES'){
          input message: 'Deploy to Prod?'
        }
      }
    }
  }
}
