---
title: "Compiler Warning (level 1) CS3018"
ms.custom: na
ms.date: 10/01/2016
ms.devlang: 
  - CSharp
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
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
# Compiler Warning (level 1) CS3018
'type' cannot be marked as CLS-Compliant because it is a member of non CLS-compliant type 'type'  
  
 This warning occurs if a nested class with the CLSCompliant attribute set to `true` is declared as a member of a class declared with the CLSCompliant attribute set to `false`. This is not allowed, since a nested class cannot be CLS-compliant if it is a member of an outer class that is not CLS-compliant. To resolve this warning, remove the CLSCompliant attribute from the nested class, or change it from `true` to `false`. For more information on CLS Compliance, see [Writing CLS-Compliant Code](assetId:///4c705105-69a2-4e5e-b24e-0633bc32c7f3) and [Language Independence and Language-Independent Components](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Example  
 The following sample generates CS3018.  
  
```  
// CS3018.cs  
// compile with: /target:library  
using System;  
  
[assembly: CLSCompliant(true)]  
[CLSCompliant(false)]  
public class Outer  
{  
   [CLSCompliant(true)]   // CS3018  
   public class Nested {}  
  
   // OK  
   public class Nested2 {}  
  
   [CLSCompliant(false)]  
   public class Nested3 {}  
}  
```