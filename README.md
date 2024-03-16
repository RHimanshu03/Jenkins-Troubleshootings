# Jenkins-Troubleshootings

1.) use command to stop jenkins services 

sudo systemctl stop jenkins 

2.) you will have to modify the "config.xml" file.

Disabling Security
One may accidentally set up security realm / authorization in such a way that you may no longer able to reconfigure Jenkins.

When this happens, you can fix this by the following steps:

Stop Jenkins (the easiest way to do this is to stopthe servlet container.)
Go to $JENKINS_HOME in the file system and find config.xml file.
Open this file in the editor.
Look for the <useSecurity>true</useSecurity> element in this file.
Replace true with false
Remove the elements authorizationStrategy and securityRealm
Start Jenkins
When Jenkins comes back, it will be in an unsecured mode where everyone gets full access to the system.
If this is still not working, trying renaming or deleting config.xml.



- But in some case it might give you an error like you don't have necessary permissions to make the change.

Therefore you can simply copy paste the below command 

sed -i 's/<useSecurity>true<\/useSecurity>/<useSecurity>false<\/useSecurity>/g' /var/lib/jenkins/config.xml

it will simply modify the file 


3.) restart the jenkins services by using below command :

service jenkins restart


It's Done !!!
