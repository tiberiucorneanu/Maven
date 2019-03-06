```
<profile>
  		<id>test</id>
  		<build>
  			<plugins>
  				<plugin>
  					<artifactId>maven-antrun-plugin</artifactId>
  					<executions>
  						<execution>
  							<phase>test</phase>
  							<goals>
  								<goal>run</goal>
  							</goals>
  							
  							<configuration>
  								<tasks>
  									<delete file="${project.build.outputDirectory}/application.properties"/>
  									<delete file="${project.build.outputDirectory}/application.prod.properties"/>
  									<copy file="src/main/resources/application.test.properties"
  										tofile="${project.build.outputDirectory}/application.properties"/>
  									<delete file="${project.build.outputDirectory}/application.test.properties"/>
  								</tasks>
  							</configuration>
  						</execution>
  					</executions>
  				</plugin>
  				
  				<plugin>
  					<artifactId>maven-surfire-plugin</artifactId>
  					<configuration>
  						<skip>true</skip>
  					</configuration>
  				</plugin>
  				
  				<plugin>
  					<artifactId>maven-jar-plugin</artifactId>
  					<executions> 
  						<execution>
  							<phase>package</phase>
  							<goals>
  								<goal>jar</goal>
  							</goals>
  							<configuration>
  								<classifier>prod</classifier>
  							</configuration>
  						</execution>
  					</executions>
  				</plugin>
  			</plugins>
  		</build>
  	</profile>
```

It seams that will display an error in CMD in this situation `mvn -Ptest clean package`   
  
[ERROR] Error resolving version for plugin 'org.apache.maven.plugins:maven-surfire-plugin' from the repositories [local (C:\Users\tcorneanu\.m2\repository), central (https://repo.maven.apache.org/maven2)]: Plugin not found in any plugin repository
