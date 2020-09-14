node("master") {

  def userInput = input(
    id: 'userInput', message: 'Inputs', parameters: [
      [$class: 'TextParameterDefinition', defaultValue: 'qa', description: 'Environment', name: 'envi'],
      listGitBranches(branchFilter: '.*',
                      credentialsId: '',
                      defaultValue: '',
                      name: 'infraBranch',
                      quickFilterEnabled: false,
                      remoteURL: 'ssh://git@github.com:jenkinsci/list-git-branches-parameter-plugin.git',
                      selectedValue: 'NONE',
                      sortMode: 'NONE',
                      tagFilter: '*',
                      type: 'PT_BRANCH')
    ]
  )
  
  echo "${userInput}"
}
