# Supported-Scenarios #

 - project structures
  - single package (flat folder structure)
  - multiple packages (multiple folders)
 - features
  - support fo 'additionalFiles' (ItemGroup to provide additional files inside a package)
  - support for TFS-Build OutDir
  - support for Visual Studio projects with content files
  - support for Visual Studio projects with linked content files

## Test folder structure ##

__Categories__

 - FileSystem convention  
_tests which try to cover different szenarious to collect files based on a folder structure convention._

 - Nuget convention  
_tests wich try to cover different szenarious inside nuspec files._

 - VisualStudio integration  
_tests which try to cover different szenarious to collect files based on visual studio project conventions using CONTENT itemgroup._

### FileSystem Convention ###

 - MultiplePackages
 - SinglePackage
   - withAdditionalFilesProj
   - withAdditionalFilesProps

### Visual Studio Integration ###

 - OutDirSupport (Support for TFS-Build 'OutDir' override)
 - ProjectSupport
  - ContentFile support
  - LinkedContentFile support