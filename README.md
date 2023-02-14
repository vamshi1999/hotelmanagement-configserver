# hotelmanagement-configserver
Configuration Server for Hotel Management Application


**Help**
Config Server:-(externalizing configurations)
@EnableConfigServer

-->Add ConfigServer dependency in configServer application, and add ConfigClient dependency in client applications
-->We have to configure each service separately
-->Instead of doing that we can add a Config server, where we add all the configurations for all services in this application

	==> GitHub --------> ConfigServer ----------> Services
	
to get the configurations from github file, In application.yml file of config server, add
	spring.cloud.config.server.git.uri: //link of the github repository where you have configs
	....git.clone-on-start: true
	
And in the client service application.yml, add
	spring:
		config:
			import: configserver:http://localhost:<configServer portname>
			
-->If we set spring.profiles.active: prod ==> It will use application-prod.yml from github
