WEBSITE: README.TXT


(=================CONNECT TO BOOKS DATABASE=========================) 

1) After exporting Website.war into Eclipse, open the WebContent folder, then the export folder
2) Get the location of the Books database in export folder by right-clicking and selecting Properties
3) Copy the location for later use
4) Find the context.xml file in META-INF folder under WebContent
5) Replace url after ‘jdbc:derby:’ with the copied location of the Books database
6) Save the changes to context.xml



(================SETTING UP SSL==========================) 

1)Generate keystore by using Java keytool: keytool -genkey -alias mydomain -keyalg RSA 
2) Put under  <!-- Define a SSL/TLS HTTP/1.1 Connector on port 8443      
  
This connector uses the NIO implementation that requires the JSSE style configuration. 
When using the APR/native implementation, the OpenSSL style configuration is required as described in the APR/native documentation -->

3)In server.xml under tomcat directory /conf, use:

<Connector
 protocol="HTTP/1.1" port="8443" maxThreads="200"
 scheme="https" secure="true" SSLEnabled="true"
	keystoreFile="C:\Users\Y500-Randy\Desktop\eclipse-jee-luna-SR2-win32-x86_64\eclipse\test.keystore" keystorePass="password" clientAuth="false" sslProtocol="TLS"/>

where "keystoreFile" refer to keystore location.


(=============CREATING LINK TO SOAP WEB SERVICE1=============================) 

1)Export the Website_Test.war file (which contains the SOAP web service)
2) Initially run TestClient.jsp in sampleProductCatalogProxy
3) Copy the link of currently-running jsp page for later use
3) Now, go to WebContent in Website project and find and open partner.jspx
4) Replace the link in anchor tag with the copied link
5) Save and run it
