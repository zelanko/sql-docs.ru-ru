---
title: Инициализация объектов пользовательских сборок | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97ee8e554fa246848b64ebafb0961f35d65f15c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63264720"
---
# <a name="initializing-custom-assembly-objects"></a>Инициализация объектов пользовательских сборок
  В некоторых случаях может понадобиться инициализировать значения свойств и полей в классах пользовательских сборок при создании их экземпляров. Вероятнее всего, понадобится инициализировать пользовательские классы значениями, доступными из коллекции глобальных объектов отчета. Это выполняется переопределением метода **OnInit** объекта **Code** отчета. Для доступа к методу **OnInit** используется элемент **Code** определения отчета. Существует два способа инициализации значений свойств или полей классов в пользовательской сборке, которую планируется использовать в отчете. Можно объявить и создать новый экземпляр класса с помощью **OnInit**, или вызвать общедоступный метод с помощью **OnInit**.  
  
## <a name="global-object-collections-and-initialization"></a>Коллекции глобальных объектов и инициализация  
 Имеется несколько доступных коллекций для инициализации переменных пользовательского класса. Можно использовать коллекции **Globals** и **User**. Коллекции **Parameters**, **Fields** и **ReportItems** недоступны пользователю во время жизненного цикла отчета, если вызван метод **OnInit**. Чтобы использовать общие коллекции **Globals** или **User**, нужно включить ссылку на объект **Report**. Например, для инициализации пользовательского класса на основании текущего языка пользователя, обращающегося к отчету, элемент **Code** может выглядеть следующим образом:  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Одним из способов инициализации значений свойств и полей класса, как показано выше, является объявление класса и создание его нового экземпляра вызовом переопределенного конструктора.  
  
 Другим способом инициализации значений свойств и полей классов пользовательских сборок является вызов общедоступного метода, определяемого на основании метода **OnInit**. Вначале необходимо добавить имя экземпляра класса в файл определения отчета. После добавления нужной ссылки на сборку и имени экземпляра можно вызвать метод инициализации, чтобы инициализировать значения свойств и полей этого класса. Метод **OnInit** может выглядеть следующим образом:  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Дополнительные сведения о добавлении ссылки на сборку и имени экземпляра для класса см. в разделе [Добавление в отчет ссылки на сборку (службы SSRS)](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 Дополнительные сведения о глобальных коллекциях объектов см. в разделе [Встроенные коллекции в выражениях (построитель отчетов и службы SSRS)](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>См. также  
 [Использование пользовательских сборок с отчетами](using-custom-assemblies-with-reports.md)  
  
  
