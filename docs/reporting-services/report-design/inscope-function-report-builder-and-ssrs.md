---
title: "Функция InScope (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Функция InScope (построитель отчетов и службы SSRS)
  Указывает, входит ли текущий экземпляр элемента в указанную область.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Синтаксис  
  
```  
InScope(scope)  
```  
  
#### Параметры  
 *область*  
 (**String**) Имя набора данных, области данных или группы, определяющей область.  
  
## Тип возвращаемых данных  
 Возвращает **Boolean**.  
  
## Замечания  
 Функция **InScope** проверяет область текущего экземпляра элемента отчета на членство в области, указанной параметром *scope*.  
  
 Значением*Scope* не может быть выражение.  
  
 Обычно функция **InScope** применяется в областях данных с динамическим определением области действия. Например, функция **InScope** может использоваться в ссылке детализации в ячейках области данных, чтобы предоставить другое название отчета и другие наборы параметров в зависимости от выбранной ячейки. Далее приведен пример.  
  
-   Следующее выражение, используемое в качестве названия отчета в ссылке детализации, открывает отчет `ProductDetail` , если выбранная ячейка находится в группе `Month` , и отчет `ProductSummary` — в противном случае.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Следующее выражение, используемое в свойстве **Omit** параметра детализированного отчета, передает параметр целевому отчету только в том случае, если выбранная ячейка находится в группе `Product`.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md).  
  
## Пример  
 Следующий пример кода показывает, находится ли данный экземпляр элемента в пределах набора данных, области данных или в области группы `Product` .  
  
```  
=InScope("Product")  
```  
  
## См. также  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  