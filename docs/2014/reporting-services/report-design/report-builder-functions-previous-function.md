---
title: Функция Previous (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 65f8f0bdc7db2e58efd27522a93e4edf6c4e0bf3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189696"
---
# <a name="previous-function-report-builder-and-ssrs"></a>Функция Previous (построитель отчетов и службы SSRS)
  Возвращает значение или значение статистического выражения для предыдущего экземпляра элемента внутри заданной области.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *expression*  
 (`Variant` или `Binary`) выражение, используемое для идентификации данных, для которого необходимо получить предыдущее значение, например, `Fields!Fieldname.Value` или `Sum(Fields!Fieldname.Value)`.  
  
 *область*  
 (`String`) Необязательно. Имя группы или области данных или значение null (`Nothing` в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), указывающее область, из которого необходимо получить предыдущее значение, определяемое *выражение*.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает `Variant` или `Binary`.  
  
## <a name="remarks"></a>Примечания  
 Функция `Previous` возвращает предыдущее значение для выражения, которое вычисляется в указанной области после применения всех операций сортировки и фильтрации.  
  
 Если *выражение* не содержит статистической функции, `Previous` по умолчанию относится к текущей области элемента отчета.  
  
 В группе подробностей используйте `Previous` для указания значения ссылки на поле в предыдущем экземпляре строки детализации.  
  
> [!NOTE]  
>  `Previous` Функция поддерживает только ссылки на поля в группе подробностей. Например, для текстового поля в группе подробностей выражение `=Previous(Fields!Quantity.Value)` возвращает данные для поля `Quantity` из предыдущей строки. Это выражение в первой строке возвращает значение NULL (`Nothing` в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).  
  
 Если *выражение* содержит агрегатную функцию, использующую область по умолчанию, `Previous` статистических выражений в пределах предыдущего экземпляра области данных, указанной в агрегатной функции.  
  
 Если *выражение* содержит агрегатную функцию, задающую область, по умолчанию *область* параметр `Previous` функции должен включать область для области, указанной в вызов агрегатной функции.  
  
 Функции `Level`, `InScope`, `Aggregate` и `Previous` не может использоваться в *выражение*параметра. Параметр *recursive* для агрегатных функций не поддерживается.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 Следующий пример кода, помещенный в строку данных по умолчанию для области данных, предоставляет значение для поля `LineTotal` в предыдущей строке.  
  
### <a name="code"></a>Код  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Описание  
 В следующем примере показано выражение, вычисляющее сумму продаж в указанный день месяца и предыдущее значение в тот же день месяца в прошлом году. Выражение добавляется в ячейку строки, относящуюся к дочерней группе `GroupbyDay`. Ее родительской группой является `GroupbyMonth`, которая имеет родительскую группу `GroupbyYear`. Выражение отображает результаты для группы GroupbyDay (область по умолчанию) и затем для группы `GroupbyYear` (родитель родительской группы `GroupbyMonth`).  
  
 Рассмотрим для примера область данных с родительской группой `Year`и ее дочерней группой `Month`, у которой имеется дочерняя группа `Day` (три вложенных уровня). Выражение `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` в строке, связанной с группой `Day` , возвращает значение продаж в тот же день и в тот же месяц прошлого года.  
  
### <a name="code"></a>Код  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>См. также  
 [Выражения используются в отчетах &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для итогов, статистических функций и встроенных коллекций &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  