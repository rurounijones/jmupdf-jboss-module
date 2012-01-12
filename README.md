# About

This is an attempt at getting JMuPDF working in JBoss AS7 as a global module. 

It is work in progress by someone who does not know what he is doing, be warned.

Currently the files in this repository will need to be copied to the following path:

$JBOSS_HOME/modules/com/jmupdf/main/

You will need to create these directories yourself.

After that you will need to edit your domain/standalone.xml file and edit/add the following:

	<subsystem xmlns="urn:jboss:domain:ee:1.0">
		<global-modules>
			<module name="com.jmupdf" slot="main" />            
		</global-modules> 		
	</subsystem>

After lots of messing about I have got to the point that the (first of many) application using this global module
fails with the error of:

17:24:05,065 ERROR [org.jboss.msc.service.fail] (MSC service thread 1-1) MSC00001: Failed to start service jboss.deployment.unit."test-knob.yml"."service ".PersonalizationGenerator.create: org.jboss.msc.service.StartException in service jboss.deployment.unit."test01-knob.yml"."service ".PersonalizationGenerator.create: org.jruby.exceptions.RaiseException: (NameError) cannot load Java class com.jmupdf.pdf.PdfDocument

Which may look terrible...but was better than before, trust me.

# Assumptions

1. I believe the problem at the moment may be a lack of 'exports' in the module.xml file.
2. Another possibility is that the native libraries are not being picked up at the Java level and this is bubbling up as a class error.



