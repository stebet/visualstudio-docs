---
title: "Data type(s) of the type parameter(s) in method &#39;&lt;methodname&gt;&#39; cannot be inferred from these arguments because more than one type is possible"
ms.custom: na
ms.date: 10/10/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4bf408c-ca1f-44ad-855a-3df898de60c6
caps.latest.revision: 9
manager: douge
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# Data type(s) of the type parameter(s) in method &#39;&lt;methodname&gt;&#39; cannot be inferred from these arguments because more than one type is possible
Data type(s) of the type parameter(s) in method '<methodname\>' cannot be inferred from these arguments because more than one type is possible. Specifying the data type(s) explicitly might correct this error.  
  
 An attempt has been made to use type inference to determine the type or types of the type parameter or parameters in a call to a generic procedure. The compiler finds more than one possible data type for one or more of the type parameters, and it reports this error.  
  
> [!NOTE]
>  When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.  
  
 The following code demonstrates the error.  
  
```vb#  
Option Strict Off  
Module Module1  
    Sub Main()  
        '' Not valid.  
        'targetMethod(1, "2")  
    End Sub  
  
    Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T)  
    End Sub  
  
End Module  
```  
  
 **Error ID:** BC36654 (within LINQ queries) and BC36651 (outside queries)  
  
### To correct this error  
  
-   If the error appears outside of a query, try specifying the data type of the type parameter explicitly:  
  
    ```  
    targetMethod(Of Integer)(1, "2")  
    ```  
  
## See Also  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)