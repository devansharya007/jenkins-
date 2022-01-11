# jenkins-
[Solved] Error: Package: jenkins-2.303.1-1.1.noarch (jenkins) Requires: daemonize --skip-broken to work
[Solved] Error: Package: jenkins-2.303.1-1.1.noarch (jenkins) Requires: daemonize --skip-broken to work
Issue:- 

The issue occurs when trying to install the jenkins on the Centos7 EC2 Instance in the AWS.

 # yum install jenkins -y


Error:- 

 --> Finished Dependency Resolution  
 Error: Package: jenkins-2.303.1-1.1.noarch (jenkins)  
       Requires: daemonize  
  You could try using --skip-broken to work around the problem  
  You could try running: rpm -Va --nofiles --nodigest  


Cause:-

Basically daemonize runs a command as a Daemon in the Centos. Since the package is missing in the version of the Centos you running thats why this error is coming. Think of it like a dependency which is required by the Jenkins to run but since you missing on the Daemonize thats why its giving the error.



Resolution:-

Daemonize doesn't ship in the default repository thats why yum is not able to resolve it. You will need to install the Daemonize from the Epel repository which is the extra package for enterprise linux as

 # yum install epel-release -y  
 # yum install daemonize -y  
 Than you can continue on installing the Jenkins as  
 # yum install jenkins -y  
