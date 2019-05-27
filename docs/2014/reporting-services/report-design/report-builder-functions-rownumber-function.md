---
title: Функция RowNumber (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d4a06a24525b3d9d0c4e4a5f3f0b749a7db70261
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66105169"
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
 (`String`) Имя набора данных, области данных, группирования или значение NULL (`Nothing` в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), указывающее контекст, в котором вычисляется количество строк. Значение `Nothing` указывает самый внешний контекст, обычно набор данных отчета.  
  
## <a name="remarks"></a>Примечания  
 `RowNumber` Возвращает текущее значение количества строк в указанной области, так же, как [RunningValue](report-builder-functions-runningvalue-function.md) возвращает текущее значение агрегатной функции. При указании области указывается и момент, когда счетчик строк сбрасывается в значение 1.  
  
 Значение*scope* не может быть выражением. Значение*scope* должно быть содержащей областью. Типичными областями — от самой внешней до самой внутренней — являются набор данных отчета, область данных, группы строк и столбцов.  
  
 Чтобы увеличить значения по столбцам, укажите область, являющуюся именем группы столбцов. Чтобы увеличить числа в строках, укажите область, являющуюся именем группы строк.  
  
> [!NOTE]  
>  Не поддерживается включение агрегатов, которые в одном выражении указывают и группу строк, и группу столбцов.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Пример кода  
 Ниже приведено выражение, которое можно использовать в свойстве `BackgroundColor` строки сведений области данных табликса, чтобы изменять цвет строк со сведениями для каждой группы, всегда начиная с белого.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>См. также  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
