---
title: "CLS Compliance Warning CLS01109"
ms.custom: na
ms.date: 10/02/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bfd6fcf-95bb-4f13-8090-5303eebb3c06
caps.latest.revision: 8
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
# CLS Compliance Warning CLS01109
All types appearing in a signature shall be CLS-compliant  
  
 Make sure that all types appearing in a member function signature are CLS-compliant.  
  
 The following sample generates CLS01109:  
  
```  
// CLS01109.cpp  
// compile with: /clr /c  
[assembly:System::CLSCompliant(true)];  
  
[System::CLSCompliant(false)]  
public ref class NotCompliantType {};  
  
public ref class MyClass {  
public:  
   property array< NotCompliantType^ >^ SomeProperty {   // CLS01109  
      array< NotCompliantType^ >^ get() { return nullptr; }  
      void set(array< NotCompliantType^ >^ v ) { }  
   }  
};  
```  
  
 Possible resolution:  
  
```  
// CLS01109b.cpp  
// compile with: /clr /LD  
[assembly:System::CLSCompliant(true)];  
  
public ref class CompliantType {};  
  
public ref class MyClass {  
public:  
   property array< CompliantType^ >^ SomeProperty {  
      array< CompliantType^ >^ get() { return nullptr; }  
      void set(array< CompliantType^ >^ v ) { }  
   }  
};  
```