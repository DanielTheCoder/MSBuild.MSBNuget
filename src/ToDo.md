New Features
 - ERROR if legacy nuget package restore is used .nuget folder with nuget.ext, nuget.targets and imports because of MSBuild it cannot be supported
 - support content files
 - support linked files




__new pipeline__

 - validation
  - depents on $(ValidationDependsOn)
 - harvest content files to 'nuget-package-stage'
  - depents on $(HarvestFilesDependsOn)
 - package harvested files
  - depends on $(PackageFiles)
 - (optional)
  - copy to release folder
  - publish to nuget


__$(ValidationDependsOn)__

 - Warnings for old MSBNuget property versions
 - Error for Nuget legacy package restore

__$(HarvestFilesDependsOn)__

 - VisualStudioContentFiles
 - VisualStudioLinkedContentFiles
 - additionalFilesFromItemGroup (MSBuild ItemGroup)
 - Filesystem relative paths

