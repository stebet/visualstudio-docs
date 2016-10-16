---
title: "&#39;Handles&#39; in classes must specify a &#39;WithEvents&#39; variable, &#39;MyBase&#39;, &#39;MyClass&#39; or &#39;Me&#39; qualified with a single identifier"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
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
# &#39;Handles&#39; in classes must specify a &#39;WithEvents&#39; variable, &#39;MyBase&#39;, &#39;MyClass&#39; or &#39;Me&#39; qualified with a single identifier
To specify an event handler, `Handles` statements must either specify an object variable declared with the `WithEvents` keyword, or a member qualified with the `MyBase` keyword.  
  
 **Error ID:** BC31412  
  
### To correct this error  
  
1.  Use the `WithEvents` modifier to declare the variables to be used with the `Handles` statement.  
  
2.  Specify the name of an event for the current class in the base class.  
  
## See Also  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [WithEvents](../Topic/WithEvents%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)