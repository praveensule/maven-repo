# maven-repo
To make jars publically available


Step1: Create a git repository with name mvn-repo
Step2: Clone the remote repository to your local file system, In my case i have cloned it to 
	git clone https://github.com/praveensule/maven-repo.git
	git checkout master
	(my path to local repository  /home/1230587/git/maven-repo)

Step3: Create a maven project in eclipse and do necessary coding in it.
       In my case i have used as shown below 
 
  	<groupId>com.opensource.test</groupId>
  	<artifactId>Test</artifactId>
  	<version>0.0.1-SNAPSHOT</version>
  	<packaging>jar</packaging>

Step4: Create a jar for this project via cmd line. Please check the below comand

mvn install:install-file -DgroupId=com.opensource.test -DartifactId=Test -Dversion=0.0.1-SNAPSHOT -Dpackaging=jar -Dfile=/home/1230587/workspace/hadoopjobs/Test/target/Test-0.0.1-SNAPSHOT.jar -DlocalRepositoryPath=/home/1230587/git/maven-repo

Step5: commit the changes to remote repository
	(if you didnt did any configuration please do the below configuration)

	git config --global user.name "Praveen"
	git config --global user.email "praveen.sule@gmail.com"

	git add .
	git commit -m "my changes"
	git push origin master

I had some issues while pushing to remore repository i used eclipse plugin 

Step6: Create another project to test 

	<groupId>com.opensource.read</groupId>
	<artifactId>TestRead</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<repositories>
		<repository>
			<id>git-praveensule</id>
			<name>praveensule's Git based repo</name>
			<url>https://github.com/praveensule/maven-repo/raw/master/</url>
		</repository>
	</repositories>
	<dependencies>
		<dependency>
			<groupId>com.opensource.test</groupId>
			<artifactId>Test</artifactId>
			<version>0.0.1-SNAPSHOT</version>
		</dependency>
	</dependencies>

Its working be happy.

Note:Remove the first project which you have created.So that you can pull from remote repository 

Reference: http://kwebble.com/blog/2014/02/19/use-github-to-host-your-own-maven-repo



