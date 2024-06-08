groovy
pipeline {
    agent any
    stages {
        stage('Log Drive Info') {
            steps {
                script {
                    logDriveInfo()
                }
            }
        }
    }
}

@NonCPS
def logDriveInfo() {
    def roots = File.listRoots()
    roots.each { root ->
        def totalSpace = root.getTotalSpace() / 1024 / 1024 / 1024 // GB
        def freeSpace = root.getFreeSpace() / 1024 / 1024 / 1024 // GB
        def usedSpace = totalSpace - freeSpace

        println "Drive: ${root.getAbsolutePath()}"
        println "Total Space: ${totalSpace} GB"
        println "Free Space: ${freeSpace} GB"
        println "Used Space: ${usedSpace} GB"
        println "----------------------------------"
    }
}
