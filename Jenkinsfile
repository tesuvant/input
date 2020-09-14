node("master") {

  properties([parameters([listGitBranches(branchFilter: '.*', credentialsId: '', defaultValue: 'development', name: 'foo', quickFilterEnabled: false, remoteURL: 'https://github.com/tesuvant/deployments_api_test', selectedValue: 'NONE', sortMode: 'ASCENDING', tagFilter: '*', type: 'PT_BRANCH')])])
  
  def userInput = input(
    id: 'userInput', message: 'Inputs', parameters: [
//      [$class: 'TextParameterDefinition', defaultValue: 'qa', description: 'Environment', name: 'envi'],
      listGitBranches(branchFilter: '.*',
                      credentialsId: '',
                      defaultValue: '',
                      name: 'FROM_BRANCH',
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
