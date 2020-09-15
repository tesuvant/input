
// @NonCPS
def getRefs(String repoUrl) {
  def allShasRefs = ("git ls-remote -t -h" + repoUrl).execute()
  print "debug"
  def allRefs = allShasRefs.text.readLines().collect { 
    it.split()[1].replaceAll('refs/heads/', '').replaceAll('refs/tags/', '').replaceAll("\\^\\{\\}", '')
  }
  print allRefs.join(" : ")
  return allRefs
}

//  properties([parameters([listGitBranches(branchFilter: '.*', credentialsId: '', defaultValue: 'development', name: 'foo', quickFilterEnabled: false, remoteURL: 'https://github.com/tesuvant/deployments_api_test', selectedValue: 'NONE', sortMode: 'ASCENDING', tagFilter: '*', type: 'PT_BRANCH')])])

  
      node {
        def deployOptions = getRefs("https://github.com/tesuvant/tag.git").join("\n")
        def userInput = input(
          id: 'userInput', message: 'Are you prepared to deploy?', parameters: [
            [$class: 'ChoiceParameterDefinition', choices: deployOptions, description: 'Approve/Disallow deployment', name: 'deploy-check']
          ]
        )
        echo "you selected: ${userInput}"
    }
