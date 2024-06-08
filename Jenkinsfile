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

def logDriveInfo() {
    def roots = java.nio.file.FileSystems.getDefault().getRootDirectories()
    roots.each { root ->
        def totalSpace = java.nio.file.Files.getFileStore(root).getTotalSpace() / 1024 / 1024 / 1024 // GB
        def freeSpace = java.nio.file.Files.getFileStore(root).getUnallocatedSpace() / 1024 / 1024 / 1024 // GB
        def usedSpace = totalSpace - freeSpace

        echo "Drive: ${root.toString()}"
        echo "Total Space: ${totalSpace} GB"
        echo "Free Space: ${freeSpace} GB"
        echo "Used Space: ${usedSpace} GB"
        echo "----------------------------------"
    }
}