---
title: "Ссылки на сборки в RDL-файле | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 87609ab5b118eaa696f7152b25cf7e984e7f6e7f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Ссылки на сборки в RDL-файле
  Поддерживает использование сборки с пользовательским кодом в файлах определения отчета, два элемента языка определения отчетов (RDL), включенных в спецификацию языка: **CodeModules** элемент и **классы** элемента.  
  
 **CodeModules** элемент позволяет ссылаться на сборки управляемого кода в выражениях отчета. **CodeModules** — это элемент верхнего уровня, который содержит ссылку на сборку, использовать в файлах определения отчета для вызова специализированных функций. Запись в определении отчета, поддерживающая использование пользовательской сборки, может выглядеть следующим образом:  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Вместо вызова метода <xref:System.Reflection.Assembly.Load%2A> в пользовательском коде зарегистрировать пользовательские сборки, либо вручную, добавив **CodeModule** элементов в RDL-файл или с помощью **ссылки** вкладке **свойства отчета** диалогового окна. Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 **Классы** элемент поддерживает использование членов экземпляров в определении отчета. **Классы** — это элемент верхнего уровня, который содержит ссылку на имя класса и имя экземпляра. Запись в определении отчета, поддерживающая использование членов экземпляров может выглядеть следующим образом:  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Дополнительные сведения см. в разделе [доступ к Custom Assemblies Through Expressions](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
