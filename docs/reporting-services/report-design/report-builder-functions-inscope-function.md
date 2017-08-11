---
title: "Функция InScope (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d8dacf74335cafa2585168288ea88d316b23d037
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---inscope-function"></a>Функции построителя - отчета функция InScope
  Указывает, входит ли текущий экземпляр элемента в указанную область.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (**String**) Имя набора данных, области данных или группы, определяющей область.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает **Boolean**.  
  
## <a name="remarks"></a>Замечания  
 Функция **InScope** проверяет область текущего экземпляра элемента отчета на членство в области, указанной параметром *scope*.  
  
 Значением*Scope* не может быть выражение.  
  
 Обычно функция **InScope** применяется в областях данных с динамическим определением области действия. Например, функция **InScope** может использоваться в ссылке детализации в ячейках области данных, чтобы предоставить другое название отчета и другие наборы параметров в зависимости от выбранной ячейки. Далее приведен пример.  
  
-   Следующее выражение, используемое в качестве названия отчета в ссылке детализации, открывает отчет `ProductDetail` , если выбранная ячейка находится в группе `Month` , и отчет `ProductSummary` — в противном случае.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Следующее выражение, используемое в свойстве **Omit** параметра детализированного отчета, передает параметр целевому отчету только в том случае, если выбранная ячейка находится в группе `Product` .  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает, находится ли данный экземпляр элемента в пределах набора данных, области данных или в области группы `Product` .  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>См. также  
 [Использование выражений в отчетах &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для итогов, статистические выражения и встроенных коллекций &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
