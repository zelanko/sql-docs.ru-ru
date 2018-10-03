---
title: Функция InScope (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e37a25432e6e701ffd97bf95799b1a567748e1df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183794"
---
# <a name="inscope-function-report-builder-and-ssrs"></a>Функция InScope (построитель отчетов и службы SSRS)
  Указывает, входит ли текущий экземпляр элемента в указанную область.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (`String`) Имя набора данных, области данных или группы, определяющей область.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает `Boolean`.  
  
## <a name="remarks"></a>Примечания  
 `InScope` Функция проверяет область текущего экземпляра элемента отчета на членство в области, указанной параметром *область*параметра.  
  
 Значением*Scope* не может быть выражение.  
  
 Правило, используется `InScope` функция применяется в областях данных с динамическим определением области действия. Например `InScope` может использоваться в ссылке детализации в ячейках области данных для предоставления различных отчетов, имя и другие наборы параметров в зависимости от выбранной ячейки. Далее приведен пример.  
  
-   Следующее выражение, используемое в качестве названия отчета в ссылке детализации, открывает отчет `ProductDetail` , если выбранная ячейка находится в группе `Month` , и отчет `ProductSummary` — в противном случае.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Следующее выражение, используемое в `Omit` свойства параметра детализированного отчета, передает параметр целевому отчету только в том случае, если выбранная ячейка находится в `Product` группы.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает, находится ли данный экземпляр элемента в пределах набора данных, области данных или в области группы `Product` .  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>См. также  
 [Использование выражений в отчетах &#40;построитель отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатов и встроенных коллекций &#40;построитель отчетов и службы SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
