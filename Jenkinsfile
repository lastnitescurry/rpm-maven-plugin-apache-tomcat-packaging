node('rpm') {
	// Mark the code checkout 'stage'....
	stage 'Checkout'
	git 'https://github.com/lastnitescurry/rpm-maven-plugin-apache-tomcat-packaging.git'
	
	// Get the maven tool.
	// ** NOTE: This 'M3' maven tool must be configured
	// **       in the global configuration.           
	def mvnHome = tool 'M3'
	
	// Mark the code build 'stage'....
	stage 'Build'
	// Run the maven build
	sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
	//step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
	
	// Mark the code build 'stage'....
	stage 'Archive'
	stash includes: 'target/rpm/apache-tomcat/RPMS/*/*.rpm', name: 'apache-tomcat.rpm'
}