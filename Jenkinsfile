
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



def newList = stepStacks.each{entry -> newList += [ booleanParam(defaultValue: false, description: entry.value, name: entry.key) ]}


        def deployOptions = getRefs("https://github.com/tesuvant/tag").join("\n")
        def userInput = input(
          id: 'userInput', message: 'Are you prepared to deploy?', parameters: newList
        )

      node {
        echo "you selected: ${userInput}"
    }
