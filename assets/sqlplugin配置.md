1��	Ŀ¼�淶����ͼ��

2������Ŀ¼ziker�µ�pom.xml����������ã�

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
			         <!-- ɾ��ͬ���� -->
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
			         <!-- �������ݿ� -->
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
			         <!-- ������ schema -->
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
			         <!-- ��������  -->
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

3��������Ŀ���õ���PostgreSQL��������Ҫ����������������Ҫ����������ã�
	<dependency>
	   <groupId>postgresql</groupId>
	   <artifactId>postgresql</artifactId>
	   <version>9.3-1103.jdbc3</version>
	</dependency>
