MSBuild.MSBNuget
================

Easily create NuGet packages with this collection of MSBuild targets.
It uses the method described here: http://docs.nuget.org/docs/creating-packages/creating-and-publishing-a-package#From_a_convention_based_working_directory
  

HOW TO USE
-----------

- Add a new project to your solution by using the MSBuild project template (http://visualstudiogallery.msdn.microsoft.com/4b75d0cc-b693-4c1c-8105-fbaeb0714b03)
- Install nuget package MSBuild.MSBNuget
- Open build.props and configure common settings, eg:
  
```XML
  <PropertyGroup>
    <PublishToLocalNugetFeed>true</PublishToLocalNugetFeed>
    <NugkgPublishFolder>C:\Dev\_galleries\nuget\</NugkgPublishFolder>
    <NugkgPublishFolder Condition="'$(NugkgPublishFolder)'==''">$(MSBuildProjectDirectory)\..\..\Publish\</NugkgPublishFolder>
    <NugkgReleaseFolder Condition="'$(NugkgReleaseFolder)'==''">$(MSBuildProjectDirectory)\..\..\Releases\</NugkgReleaseFolder>
  </PropertyGroup>
 ```

- Use item groups to add additional files, eg:

```XML
  <ItemGroup>
    <additionalFiles Include="$(MSBuildThisFileDirectory)\..\..\MSBNuget\nuget.targets">
      <targetFolder>MSBNuget/content/.build</targetFolder>
    </additionalFiles>
  </ItemGroup>
```

- Or use convention folders (libs, tools, content, build), eg:  
  
```
project  
|-'folder: nuspecname'  
|--build  
|--content  
|--libs  
|--tools  
|-'file: nuspec'  
```
    
- Open build.targets and add/replace with the following  
  
```XML
  <Import Project="$(MSBuildThisFileDirectory)\..\..\MSBNuget\nuget.targets" />

  <Target Name="Build">
    <CallTarget Targets="NugetBuild" />
  </Target>

  <Target Name="Clean">
    <CallTarget Targets="NugetClean" />
  </Target>

  <Target Name="Rebuild">
    <CallTarget Targets="NugetRebuild" />
  </Target>

  <Target Name="Publish">
    <CallTarget Targets="NugetPublish"/>
  </Target>
```  