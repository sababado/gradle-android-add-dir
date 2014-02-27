gradle-android-add-dir
======================

A simple script to help manually inject source or test directories into a .iml file

This is a modified version of a script posted by [Bernd Bergler](https://groups.google.com/forum/#!msg/adt-dev/v0AluPBcoy0/KXR7oOmRQZIJ)

#Usage
Apply the script at the top of your build.gradle file. Make sure to define the two necessary properties before the script is applied.

|`project.ext['src.java.dir']`|Takes an array of java directories|
|`project.ext['module.iml.file']`|Takes a string with the path to the module's `.iml` file.|
	
	project.ext['src.java.dir'] = ['src/test/java']
    project.ext['module.iml.file'] = "VaDroid3.iml"
    apply from: 'gradle-android-add-dir.gradle'
	// The rest of the script
	
The script can alternatively be applied directly from it's location on Github.
	apply from: 'https://raw.github.com/sababado/gradle-android-add-dir/master/gradle-android-add-dir.gradle'