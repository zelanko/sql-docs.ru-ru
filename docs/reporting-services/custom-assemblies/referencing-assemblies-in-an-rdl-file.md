---
title: Ссылки на сборки в RDL-файле | Документы Майкрософт
description: Узнайте, как создавать ссылки на сборки в файле языка определения отчетов (RDL), в частности, в элементе CodeModules и элементе Classes.
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d310ec6895f1e8d027378fca71df36331dfbf5a8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "80217023"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Ссылки на сборки в RDL-файле
  Для поддержки использования сборок с пользовательским кодом в файлах определения отчета в спецификацию языка определения отчетов были включены два элемента: **CodeModules** и **Classes**.  
  
 Элемент **CodeModules** позволяет ссылаться на сборки с управляемым кодом в выражениях отчета. Элемент высокого уровня **CodeModules** содержит ссылку на сборку, используемую в файлах определения отчета для вызова специализированных функций. Запись в определении отчета, поддерживающая использование пользовательской сборки, может выглядеть следующим образом:  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Вместо вызова метода <xref:System.Reflection.Assembly.Load%2A> в пользовательском коде пользовательские сборки можно зарегистрировать либо вручную, добавив элементы **CodeModule** в RDL-файл, либо использовав вкладку **Ссылки** в диалоговом окне **Свойства отчета**. Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Элемент **Classes** поддерживает использование членов экземпляров в определении отчета. **Classes** — это высокоуровневый элемент, содержащий ссылку на имя класса и имя экземпляра. Запись в определении отчета, поддерживающая использование членов экземпляров может выглядеть следующим образом:  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Дополнительные сведения о доступе к коду см. в разделе [Доступ к пользовательским сборкам посредством выражений](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
