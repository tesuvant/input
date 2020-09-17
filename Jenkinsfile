def getJobName() {
  def jobNameParts = env.JOB_NAME.tokenize('/') as String[]
  return jobNameParts.length < 2 ? env.JOB_NAME : jobNameParts[jobNameParts.length - 2]
}

// @NonCPS
def getRefs(String repoUrl) {
  def allShasRefs = ("git ls-remote -t -h " + repoUrl).execute()
  def allRefs = allShasRefs.text.readLines().collect { 
    it.split()[1].replaceAll('refs/heads/', '').replaceAll('refs/tags/', '').replaceAll("\\^\\{\\}", '')
  }
  return allRefs
}

def stepStacks = [
  enable_00: 'Enable ',
  enable_01: 'Enab2'
]

    def slaveOpts = 'azure\nazure4'
    def tfWorkspaceOpts = 'prod\ndev'

def newList = []
stepStacks.each{entry -> newList += [ booleanParam(defaultValue: false, description: entry.value, name: entry.key) ]}
newList += [ $class: 'ChoiceParameterDefinition', choices: tfWorkspaceOpts, description: '222', name: 'workspace']
newList += [ $class: 'ChoiceParameterDefinition', choices: slaveOpts, description: '333', name: 'slave']


        def deployOptions = getRefs("https://github.com/tesuvant/tag").join("\n")
        def userInput = input(
          id: 'userInput', message: 'Are you prepared to deploy?', parameters: newList
        )

      node {
  //      echo "you selected: ${userInput}"
        
        echo "----"
        echo getJobName()
        echo "----"
        stage("1") {
          checkout scm
       }
       
//        assert list.findResult { it.startsWith('Gra') ? it : null } == 'Grails'
        
        myid = new File("${env.WORKSPACE}/README.md").text.tokenize('\n').findResult{it.contains('id:') ? it.split(":")[1].trim() : null}
        if(!myid) {
          echo "id not set"
        }
        //echo myid
        
     withEnv([ "ZZZ=ploo",
        "XXX=true"
      ]) {
       
       stage("2") {
          env.SSSS = "123456"
          sh """ echo \$FOOBAR """
       }
       
      }
       stage("3") {
         sh """ env | sort """
       }
        def stageSkippedText = "#!/bin/sh -e; echo -e '****************************************\nSKIPPED!\n****************************************'"
       stage("4") {
         sh "$stageSkippedText"
         stageResult: 'ABORTED'
         //unstable(message: "${STAGE_NAME} is skipped")
       }
       

    }

