---
title: "How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - VB
  - CSharp
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-ide-deployment
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
manager: wpickett
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment
A ClickOnce deployment can test for a number of prerequisites that must be available on the client computer for the ClickOnce application to run. These include the required minimum version of the .NET Framework, the version of the operating system, and any assemblies that must be preinstalled in the global assembly cache (GAC). ClickOnce, however, cannot install any of these prerequisites itself; if a prerequisite is not found, it simply halts installation and displays a dialog box explaining why the installation failed.  
  
 There are two methods for installing prerequisites. You can install them using a bootstrapper application. Alternatively, you can specify a support URL for individual prerequisites, which is displayed to users on the dialog box if the prerequisite is not found. The page referenced by that URL can contain links to instructions for installing the required prerequisite. If an application does not specify a support URL for an individual prerequisite, ClickOnce displays the support URL specified in the deployment manifest for the application as a whole, if it is defined.  
  
 While Visual Studio, Mage.exe, and MageUI.exe can all be used to generate ClickOnce deployments, none of these tools directly support specifying a support URL for individual prerequisites. This document describes how to modify your deployment's application manifest and deployment manifest to include these support URLs.  
  
### Specifying a support URL for an individual prerequisite  
  
1.  Open the application manifest (the .manifest file) for your ClickOnce application in a text editor.  
  
2.  For an operating system prerequisite, add the `supportUrl` attribute to the `dependentOS` element:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  For a prerequisite for a certain version of the common language runtime, add the `supportUrl` attribute to the `dependentAssembly` entry that specifies the common language runtime dependency:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  For a prerequisite for an assembly that must be preinstalled in the global assembly cache, set the `supportUrl` for the `dependentAssembly` element that specifies the required assembly:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Optional. For applications that target the .NET Framework 4, open the deployment manifest (the .application file) for your ClickOnce application in a text editor.  
  
6.  For a .NET Framework 4 prerequisite, add the `supportUrl` attribute to the `compatibleFrameworks` element:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Once you have manually altered the application manifest, you must re-sign the application manifest using your digital certificate, then update and re-sign the deployment manifest as well. You must use the Mage.exe or MageUI.exe SDK tools to accomplish this task, as regenerating these files using Visual Studio erases your manual changes. For more information on using Mage.exe to re-sign manifests, see [How to: Re-sign Application and Deployment Manifests](../VS_IDE/How-to--Re-sign-Application-and-Deployment-Manifests.md).  
  
## .NET Framework Security  
 The support URL is not displayed on the dialog box if the application is marked to run in partial trust.  
  
## See Also  
 [Mage.exe (Manifest Generation and Editing Tool)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../VS_IDE/Walkthrough--Manually-Deploying-a-ClickOnce-Application.md)   
 [<compatibleFrameworks\> Element](../VS_IDE/-compatibleFrameworks--Element--ClickOnce-Deployment-.md)   
 [ClickOnce and Authenticode](../VS_IDE/ClickOnce-and-Authenticode.md)   
 [Application Deployment Prerequisites](../VS_IDE/Application-Deployment-Prerequisites.md)