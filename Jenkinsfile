node("master") {

  def userInput = input(
    id: 'userInput', message: 'Inputs', parameters: [
      [$class: 'TextParameterDefinition', defaultValue: 'qa', description: 'Environment', name: 'envi'],
      listGitBranches(branchFilter: '.*',
                      credentialsId: '',
                      defaultValue: 'development',
                      name: 'infraBranch',
                      quickFilterEnabled: false,
                      remoteURL: 'https://github.com/tesuvant/helloworld2.git',
                      selectedValue: 'NONE',
                      sortMode: 'ASCENDING',
                      tagFilter: '*',
                      type: 'PT_BRANCH')
    ]
  )
  
  echo "${userInput}"
}
