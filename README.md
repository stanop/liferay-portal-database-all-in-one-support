![travis ci](https://travis-ci.org/amusarra/liferay-portal-database-all-in-one-support.svg?branch=master)

# Welcome to Liferay CE 7.0 Database All In One Support

[![Join the chat at https://gitter.im/amusarra/liferay-portal-oracledb-support](https://badges.gitter.im/amusarra/liferay-portal-database-all-in-one-support.svg)](https://gitter.im/amusarra/liferay-portal-database-all-in-one-support?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Those who follow Liferay is aware of the fact that the Community Edition version 7 of Liferay, were eliminated quite a bit of components App Server, Database & Clustering Support. For more detail information you can read the blog post by [Bryan Cheung]( https://www.liferay.com/it/web/bryan.cheung/blog/-/blogs/liferay-portal-7-ce-app-server-database-clustering-support) published on April 7, 2016.

The Liferay 7 CE no more support OOTB (Out Of The Box):
* Application Server: Oracle WebLogic, IBM WebSphere
* Clustering
* MultiVM Cache
* Oracle Database, Microsoft SQL Server, IBM DB2, Sybase DB

This project add support to the Oracle database. Liferay has performed refactorting the code so that it is possible and easy to add support for databases no longer supported OOTB

## 1. Build project
Requirements for build project
1. Sun/Oracle JDK 1.8
2. Maven 3.x (for build project) or Gradle 2.x

The driver that adds support for Oracle, SQLServer and DB2 database is a jar (**liferay-portal-database-all-in-one-support-${version}.jar**) which then will be installed in ROOT/WEB-INF/lib (for apache tomcat).

To generate the all in one driver just follow the instructions below.

You can download the binary jar [liferay-portal-oracledb-support-1.0-SNAPSHOT.jar](https://github.com/amusarra/liferay-portal-oracledb-support/releases/download/v1.0/liferay-portal-oracledb-support-1.0-SNAPSHOT.jar), by doing so you can avoid doing the build.

```
$ git clone https://github.com/amusarra/liferay-portal-database-all-in-one-support.git
$ cd liferay-portal-database-all-in-one-support
$ mvn package
```

the build process create the jar inside the (maven) target directory:

```
liferay-portal-database-all-in-one-support-${version}.jar
```

## 2. Configure

Below you can see the portal-ext.properties

```
##
## Admin Portlet
##
    #
    # Configure email notification settings.
    #
    admin.email.from.name=Joe Bloggs
    admin.email.from.address=test@liferay.com

##
## JDBC
##

    #
    # Oracle
    #
    # jdbc.default.driverClassName=oracle.jdbc.OracleDriver
    # jdbc.default.username=liferayce7
    # jdbc.default.password=liferay12345
    # jdbc.default.url=jdbc:oracle:thin:@oracledb.vm.local:1521:xe

    #
    # DB2
    #
	  # jdbc.default.driverClassName=com.ibm.db2.jcc.DB2Driver
    # jdbc.default.url=jdbc:db2://db2.vm.local:50001/lportal:deferPrepares=false;fullyMaterializeInputStreams=true;fullyMaterializeLobData=true;progresssiveLocators=2;progressiveStreaming=2;
    # jdbc.default.username=db2inst1
	  # jdbc.default.password=system

    #
    # SQL Server
    #
    # jdbc.default.driverClassName=com.microsoft.sqlserver.jdbc.SQLServerDriver
    # jdbc.default.username=liferay
    # jdbc.default.password=liferay12345
    # jdbc.default.url=jdbc:sqlserver://sqlserverdb.vm.local;databaseName=liferayce7


##
## Liferay Home
##
    #
    # Specify the Liferay home directory.
    #
    liferay.home=/opt/liferay-ce-portal-7.0-ga3

##
## Setup Wizard
##
    #
    # Set this property to true if the Setup Wizard should be displayed the
    # first time the portal is started.
    #
    setup.wizard.enabled=false
```