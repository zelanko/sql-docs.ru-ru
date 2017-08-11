---
title: "Инициализация объектов пользовательских сборок | Документы Microsoft"
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
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ab05efc7baba58a34180faa038cb58c7f57f4af2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="initializing-custom-assembly-objects"></a>Инициализация объектов пользовательских сборок
  В некоторых случаях может понадобиться инициализировать значения свойств и полей в классах пользовательских сборок при создании их экземпляров. Вероятнее всего, понадобится инициализировать пользовательские классы значениями, доступными из коллекции глобальных объектов отчета. Это делается путем переопределения **OnInit** метод **кода** объекта отчета. Чтобы получить доступ к **OnInit**, используйте **кода** элемент определения отчета. Существует два способа инициализации значения свойства или поля из классов в пользовательской сборке, которую планируется использовать в отчете: можно объявить и создать новый экземпляр класса с помощью **OnInit**, может вызвать общедоступный метод с помощью **OnInit**.  
  
## <a name="global-object-collections-and-initialization"></a>Коллекции глобальных объектов и инициализация  
 Имеется несколько доступных коллекций для инициализации переменных пользовательского класса. Можно использовать **Globals** и **пользователя** коллекций. **Параметры**, **поля** и **ReportItems** коллекции не доступны на точке в жизненный цикл отчета при **OnInit** вызывается метод. Чтобы использовать общие наборы **Globals** или **пользователя**, необходимо включить **отчетов** ссылку на объект. Например, для инициализации пользовательского класса на основе текущего языка пользователя, обращающегося к отчету, ваш **кода** элемент может выглядеть следующим образом:  
  
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
  
 Другой способ инициализации значений свойств и полей классов пользовательских сборок является вызов общедоступного метода, определяемого на основании **OnInit** метод. Вначале необходимо добавить имя экземпляра класса в файл определения отчета. После добавления нужной ссылки на сборку и имени экземпляра можно вызвать метод инициализации, чтобы инициализировать значения свойств и полей этого класса. Ваш **OnInit** метод может выглядеть следующим образом:  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Дополнительные сведения о добавлении ссылок и экземпляр имя сборки для пользовательского класса см. в разделе [добавления ссылки на сборку в отчет &#40; Службы SSRS &#41; ](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 Дополнительные сведения о коллекциях глобальных объектов см. в разделе [встроенные коллекции в выражениях &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
