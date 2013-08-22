Why this project
===========

JDK7 uses sun.nio.fs.GnomeFileTypeDetector as the default filetype detector on mac OSX. However this implementation is buggy and won't detect anything, even if libgio is actually available on the system. This project is a dirty backports of JDK8's MimeTypesFileTypeDetector which defaults to ${user.home}/.mime.types for mime types mapping and is not customisable at runtime.

How to use
============

Run maven clean package and make sure it is on the classpath of your app (I drop the resulting jar in my `$JAVA_HOME/jre/lib/ext` folder to avoid polluting the project itself).
The jar will automatically register the backported file type detector. 
Make sure you have an existing ~/.mime.types, if necessary create one from the file at the root of this project.

