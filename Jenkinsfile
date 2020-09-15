
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
  enable_01: 'Ena',
  enable_02: 'En',
  enable_03: 'Enabl',
  enable_04: 'Enable ',
  enable_06: 'Enab',
  enable_08: 'Enable ',
  enable_09: 'Ena'
]


stepStacks.each{entry -> [ booleanParam, defaultValue: false, description: $entry.value, name: $entry.value ],}

        def deployOptions = getRefs("https://github.com/tesuvant/tag").join("\n")
        def userInput = input(
          id: 'userInput', message: 'Are you prepared to deploy?', parameters: [
            stepStacks.each{entry -> [ booleanParam, defaultValue: false, description: $entry.value, name: $entry.value ],}
          ]
        )

      node {
        echo "you selected: ${userInput}"
    }
