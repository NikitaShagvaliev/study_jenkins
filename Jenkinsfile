import java.io.File
import groovy.json.JsonOutput

def getDriveInfo() {
    def drivesInfo = []
    File.listRoots().each { file ->
        def totalSpace = file.getTotalSpace()
        def freeSpace = file.getFreeSpace()
        def usedSpace = totalSpace - freeSpace
        
        def driveInfo = [
            path      : file.path,
            totalSpace: formatSize(totalSpace),
            usedSpace : formatSize(usedSpace),
            freeSpace : formatSize(freeSpace)
        ]
        
        drivesInfo << driveInfo
    }
    return drivesInfo
}

def formatSize(size) {
    def unit = 1024
    if (size < unit) return "${size} B"
    int exp = (int) (Math.log(size) / Math.log(unit))
    String pre = "KMGTPE".charAt(exp - 1).toString()
    return String.format("%.1f %sB", size / Math.pow(unit, exp), pre)
}

def logDriveInfo() {
    def logger = new File('drive_info.log')
    def drivesInfo = getDriveInfo()
    
    logger.text = JsonOutput.prettyPrint(JsonOutput.toJson(drivesInfo))
    println JsonOutput.prettyPrint(JsonOutput.toJson(drivesInfo))
}

// Execute the logging function
logDriveInfo()
