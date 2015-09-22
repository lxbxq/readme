1、	目录规范见上图；

2、在总目录ziker下的pom.xml添加如下配置；

<build>
      <finalName>ziker</finalName>
			<plugins>
			   <!-- sql plugins -->
			   <plugin>
			      <groupId>org.codehaus.mojo</groupId>
			      <artifactId>sql-maven-plugin</artifactId>
			      <dependencies>
			         <dependency>
			            <groupId>postgresql</groupId>
			            <artifactId>postgresql</artifactId>
			            <version>9.3-1103.jdbc3</version>
			         </dependency>
			      </dependencies>
			      <executions>
			         <!-- 删除同名库 -->
			         <execution>
			            <id>drop-db-before-test-if-any</id>
			            <phase>process-test-resources</phase>
			            <goals>
			               <goal>execute</goal>
			            </goals>
			            <configuration>
			               <!-- need another database to drop the targeted one -->
			               <driver>org.postgresql.Driver</driver>
			               <url>jdbc:postgresql://127.0.0.1:5432/postgres</url>
			               <username>postgres</username>
			               <password>postgres</password>
			               <autocommit>true</autocommit>
			               <sqlCommand>drop database test2</sqlCommand>
			               <!-- ignore error when database is not avaiable -->
			               <onError>continue</onError>
			            </configuration>
			         </execution>
			         <!-- 创建数据库 -->
			         <execution>
			            <id>create-db</id>
			            <phase>process-test-resources</phase>
			            <goals>
			               <goal>execute</goal>
			            </goals>
			            <configuration>
			               <driver>org.postgresql.Driver</driver>
			               <url>jdbc:postgresql://127.0.0.1:5432/postgres</url>
			               <username>postgres</username>
			               <password>postgres</password>
			               <autocommit>true</autocommit>
			               <sqlCommand>create database test2</sqlCommand>
			            </configuration>
			         </execution>
			         <!-- 创建表 schema -->
			         <execution>
			            <id>create-schema</id>
			            <phase>process-test-resources</phase>
			            <goals>
			               <goal>execute</goal>
			            </goals>
			            <configuration>
			               <autocommit>true</autocommit>
			               <driver>org.postgresql.Driver</driver>
			               <url>jdbc:postgresql://127.0.0.1:5432/test2</url>
			               <username>postgres</username>
			               <password>postgres</password>
			               <orderFile>ascending</orderFile>
			               <fileset>
			                  <basedir>${basedir}</basedir>
			                  <includes>
			                        <include>db/pg/share/1.0/all/Dump20150916_ddl.sql</include>
			                  </includes>
			               </fileset>
			               <!-- <srcFiles>
			                              <srcFile>../db/pg/share/1.0/Dump20150916_dll.sql</srcFile>
			                          </srcFiles> -->
			            </configuration>
			         </execution>
			         <!-- 创建数据  -->
			         <execution>
			            <id>create-data</id>
			            <phase>process-test-resources</phase>
			            <goals>
			               <goal>execute</goal>
			            </goals>
			            <configuration>
			               <autocommit>true</autocommit>
			               <driver>org.postgresql.Driver</driver>
			               <url>jdbc:postgresql://127.0.0.1:5432/test2</url>
			               <username>postgres</username>
			               <password>postgres</password>
			               <orderFile>ascending</orderFile>
			               <fileset>
			                  <basedir>${basedir}</basedir>
			                  <includes>
			                     <include>db/pg/share/1.0/all/Dump20150916_data.sql</include>
			                  </includes>
			               </fileset>
			               <!-- <srcFiles>
			                              <srcFile>../db/pg/share/1.0/Dump20150916_dll.sql</srcFile>
			                          </srcFiles> -->
			            </configuration>
			         </execution>
			         <!-- drop db after test -->
			         <!-- <execution>
			                      <id>drop-db-after-test</id>
			                      <phase>test</phase>
			                      <goals>
			                          <goal>execute</goal>
			                      </goals>
			                      <configuration>
			                          <autocommit>true</autocommit>
			                          <sqlCommand>drop database test2</sqlCommand>
			                      </configuration>
			                  </execution> -->
			      </executions>
			   </plugin>
			</plugins>
      
  </build>

3、由于项目中用到了PostgreSQL，所以需要添加驱动程序包，需要添加如下配置：
	<dependency>
	   <groupId>postgresql</groupId>
	   <artifactId>postgresql</artifactId>
	   <version>9.3-1103.jdbc3</version>
	</dependency>
