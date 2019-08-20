pipeline{
  agent any
  environment{
    def DEVELOPMENT_BRANCH = "development"
    def PRODUCTION_BRANCH = "master"
    def DEV_CONNECT_SERVER = "https://rstudioconnect-dev.bcbsfl.com/__api__/v1"
    def PROD_CONNECT_SERVER = "https://rstudioconnect.bcbsfl.com/__api__/v1"
    def CONNECT_SERVER = ""
    def DEV_CONNECT_API_KEY = "devapikey"
    def PROD_CONNECT_API_KEY = "prodapikey"
    def CONNECT_API_KEY = ""
    def CONTENT_NAME = "Test Content Name"
    def CONTENT_TITLE = "Test Content Title"
    def ORIGINAL_GUID = ""
    def isProd = "false"
  }
  stages{
    stage("Build Bundle"){
      steps{
        echo "Workspace: ${WORKSPACE}"
      }
    }
    stage("Check Development"){
      when{expression{env.BRANCH_NAME == "${DEVELOPMENT_BRANCH}"}}
      steps{
        CONNECT_SERVER = DEV_CONNECT_SERVER
        CONNECT_API_KEY = DEV_CONNECT_API_KEY
        echo "Development"
        echo CONNECT_SERVER
      }
    }
    stage("Check Production"){
      when{expression{env.BRANCH_NAME == "${PRODUCTION_BRANCH}"}}
      steps{
        CONNECT_SERVER = PROD_CONNECT_SERVER
        CONNECT_API_KEY = PROD_CONNECT_API_KEY
        isProd = true
        echo "Production"
        echo CONNECT_SERVER
      }
    }
    stage("Check Prod Approval"){
      when{expression{isProd == true}}
      steps{
        echo "Approval for branch: ${env.BRANCH_NAME}..."
        echo "Check Remedy Status"
      }
    }
    stage("Create Connect Content"){
      steps{
        echo "Create Content"
      }
    }
   }
}
