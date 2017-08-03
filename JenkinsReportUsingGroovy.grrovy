import jenkins.*
import jenkins.model.*
import hudson.*
import hudson.model.*

//Getting yesterday's date
ydate = new Date()-1
ydateFormatted = ydate.format( 'yyyy-MM-dd' )
//println ydateFormatted

//Traversing through all jobs
allJobs = Hudson.instance.getAllItems()
count = 0
allJobs.each { job ->
  if (job instanceof com.cloudbees.hudson.plugins.folder.Folder) { return }
  size = job.builds.size()
  if (size == 0) { return }
  for (i = size; i >= 0; i--)
  {
    name = job.builds[i-1].displayName
    timeStamp = job.builds[i-1].timestampString2
    status = timeStamp.contains("${ydateFormatted}")
    if (status == true ) { 
      println "ProjectName: ${job} | JobName: ${job.getName()} | BuildName: ${name} | TimeStamp: ${timeStamp}"
    count++
      }
  }
}
if (count !=0)
	println "No.of jobs ran on ${ydateFormatted}: ${count}"
else
	println "No jobs ran on ${ydateFormatted}"
