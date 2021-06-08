# ReleaseAnnotations
Release Annotations for Azure Application Insights

See https://docs.microsoft.com/en-us/azure/azure-monitor/app/annotations for basic instructions

However replace 

```powershell
-aiResourceId "<aiResourceId>" `
    -releaseName "<releaseName>" `
    -releaseProperties @{"ReleaseDescription"="<a description>";
         "TriggerBy"="<Your name>" }
 ```
 
 with
 
 ```powershell
 -aiResourceId "/subscriptions/59bdf6e9-f925-45bf-ae95-18c6d959f688/resourceGroups/ProjectPyramid/providers/microsoft.insights/components/ProjectPyramid-Local" `     
 -releaseName "$(Release.ReleaseName)" `     
 -releaseProperties @{
  "BuildNumber"="$(Build.BuildNumber)";
  "BuildRepositoryName"="$(Build.Repository.Name)";
  "BuildRepositoryProvider"="$(Build.Repository.Provider)";
  "ReleaseDefinitionName"="$(Build.DefinitionName)";
  "ReleaseDescription"="Triggered by $(Build.DefinitionName) $(Build.BuildNumber)";
  "ReleaseEnvironmentName"="$(Release.EnvironmentName)";
  "ReleaseId"="$(Release.ReleaseId)";
  "ReleaseName"="$(Release.ReleaseName)";
  "ReleaseRequestedFor"="$(Release.RequestedFor)";
  "ReleaseWebUrl"="$(Release.ReleaseWebUrl)";
  "SourceBranch"="$(Build.SourceBranch)";
  "TeamFoundationCollectionUri"="$(System.TeamFoundationCollectionUri)" }
 ```
