---
title: Функция RowNumber (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 150a46a736a9c6ddd2f8c394f3f173906cd07132
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097861"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a>Функция RowNumber (построитель отчетов и службы SSRS)
  Возвращает текущее количество строк в указанной области.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (`String`) Имя набора данных, области данных или группы или значение null (`Nothing` в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), указывающее контекст, в котором оценивается количество строк. `Nothing` Указывает самый внешний контекст, обычно набор данных отчета.  
  
## <a name="remarks"></a>Примечания  
 `RowNumber` Возвращает текущее значение количества строк в указанной области, как и [RunningValue](report-builder-functions-runningvalue-function.md) возвращает текущее значение агрегатной функции. При указании области указывается и момент, когда счетчик строк сбрасывается в значение 1.  
  
 Значение*scope* не может быть выражением. Значение*scope* должно быть содержащей областью. Типичными областями — от самой внешней до самой внутренней — являются набор данных отчета, область данных, группы строк и столбцов.  
  
 Чтобы увеличить значения по столбцам, укажите область, являющуюся именем группы столбцов. Чтобы увеличить числа в строках, укажите область, являющуюся именем группы строк.  
  
> [!NOTE]  
>  Не поддерживается включение агрегатов, которые в одном выражении указывают и группу строк, и группу столбцов.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Пример кода  
 Ниже приведен выражение, которое можно использовать для `BackgroundColor` свойства, чтобы изменять цвет строк со сведениями для каждой группы, всегда начиная с белого строки сведений области данных Табликса.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>См. также  
 [Выражения используются в отчетах &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для итогов, статистических функций и встроенных коллекций &#40;отчетов построителя отчетов и службы SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  