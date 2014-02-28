gradle-android-add-dir
======================

A simple script to help manually inject source or test directories into a `.iml` file before every build. This is required before every build because `.iml` files are regenerated before every build.

This is a modified version of a script posted by [Bernd Bergler](https://groups.google.com/forum/#!msg/adt-dev/v0AluPBcoy0/KXR7oOmRQZIJ)

#Usage
Apply the script at the top of your `build.gradle` file. Make sure to define the two necessary properties before the script is applied.

| Property | Description |
|:---------|:------------|
| `project.ext['src.java.dir']` | Takes an array of source directories |
| `project.ext['module.iml.file']` | Takes a string with the path to the module's `.iml` file. |
	
    project.ext['src.java.dir'] = ['src/test']
    project.ext['module.iml.file'] = "VaDroid3.iml"
    apply from: 'gradle-android-add-dir.gradle'
	// The rest of the build.gradle script
	
The script can alternatively be applied directly from it's location on Github.

	apply from: 'https://raw.github.com/sababado/gradle-android-add-dir/master/gradle-android-add-dir.gradle'

##Why Use This?
Android Studio dropped the ability to mark your own source directories due to [lack of gradle support](https://groups.google.com/forum/#!msg/adt-dev/v0AluPBcoy0/QEaSOgsNxCMJ). One example where this is necessary is when trying to do unit tests using robolectric. The practice is to have a src/test/java directory with unit tests in them. The IDE won't recognize this as a source directory. It can be done by manually updating the module's `.iml` file however it will be overwritten everytime a build is run.
This works very well with the [android-unit-test](https://github.com/JCAndKSolutions/android-unit-test) plugin.
##Is this a hack?
Yes. Yes it is. Until Android Studio brings back support to mark your own source directories this will be relevant. 
