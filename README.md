MSBuild.MSBNuget
=================

|master|v2|latest|
|:-:|:-:|:-:|
|[![Build status](https://ci.appveyor.com/api/projects/status/ej734224ri3aavru/branch/master?svg=true)](https://ci.appveyor.com/project/DanielTheCoder/msbuild-msbnuget/branch/master)|[![Build status](https://ci.appveyor.com/api/projects/status/ej734224ri3aavru/branch/feature/v20?svg=true)](https://ci.appveyor.com/projects/DanielTheCoder/msbuild-msbnuget/branch/feature/v20)|[![Build status](https://ci.appveyor.com/api/projects/status/ej734224ri3aavru?svg=true)](https://ci.appveyor.com/project/DanielTheCoder/msbuild-msbnuget)|

Easily create NuGet packages with this collection of MSBuild targets.
It uses the method described here: http://docs.nuget.org/docs/creating-packages/creating-and-publishing-a-package#From_a_convention_based_working_directory
  

HOW TO USE
------------

- Add a new project to your solution by using the [MSBuild-project-template](http://visualstudiogallery.msdn.microsoft.com/4b75d0cc-b693-4c1c-8105-fbaeb0714b03)
- Install nuget package [MSBuild.MSBNuget](https://www.nuget.org/packages/MSBuild.MSBNuget)
- Open build.props and configure common settings, eg:
  
```XML
  <PropertyGroup>
    <NugetPublishToReleaseFolder Condition="'$(NugetPublishToReleaseFolder)'==''">false</NugetPublishToReleaseFolder>
    <NugetPublishToLocalNugetFeed Condition="'$(NugetPublishToLocalNugetFeed)'==''">false</NugetPublishToLocalNugetFeed>

    <NugetPublishLocalNugetFeedFolder Condition="'$(NugetPublishLocalNugetFeedFolder)'==''">$(MSBuildProjectDirectory)\..\..\Publish\</NugetPublishLocalNugetFeedFolder>
    <NugetPublishReleaseFolder Condition="'$(NugetPublishReleaseFolder)'==''">$(MSBuildProjectDirectory)\..\..\Releases\</NugetPublishReleaseFolder>
  </PropertyGroup>
 ```

- Use item groups to add additional files, eg: add file 'my.dll' to convention based folder

```XML
  <ItemGroup>
    <additionalFiles Include="$(MSBuildThisFileDirectory)\..\..\MSBNuget\my.dll">
      <targetFolder>MSBNuget/content/libs/net45</targetFolder>
    </additionalFiles>
  </ItemGroup>
```

- Or use convention folders (libs, tools, content, build), eg:  
  
```
project  
|-'folder: nuspecname'  
|-|-build  
|-|-content  
|-|-libs  
|-|-tools  
|-|-'file: nuspecname.nuspec'  
|-|-'file: nuspecname.nuspec.props'  
```
    
- build.targets will be replaced during install with nuget package [MSBuild.MSBBuildConvention](https://www.nuget.org/packages/MSBuild.MSBBuildConvention)
  
Sample
------------
https://github.com/DanielTheCoder/MSBuild.MSBNuget/tree/master/src/MSBNuget.Nuget  
  

Contributing
------------
If you are interested in contributing,  
  
1. Get a Github account  
1. Fork the project  
1. Make your feature addition or bugfix. Please also update the [changelog](https://github.com/DanielTheCoder/MSBuild.MSBNuget/blob/master/changelog.txt).  
1. Send me a pull request via GitHub  
 