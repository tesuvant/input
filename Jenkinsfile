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
        stage("SCM") {
          checkout scm
       }
       
//        assert list.findResult { it.startsWith('Gra') ? it : null } == 'Grails'
        
        myid = new File("${env.WORKSPACE}/README.md").text.tokenize('\n').findResult{it.contains('id:') ? it.split(":")[1].trim() : null}
        if(!myid) {
          echo "id not set"
        }
        //echo myid
        
        
       stage("222") {
          env.FOOBAR = "123456"
          sh """ echo \$FOOBAR """
       }
        
    }

