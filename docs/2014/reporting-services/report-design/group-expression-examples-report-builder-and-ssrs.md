---
title: Примеры выражений групп (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7a1051b194c9ca9f5ad185d9759b85a252f6eec4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026585"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a>Примеры выражений групп (построитель отчетов и службы SSRS)
  В области данных можно группировать данные по одному полю или создавать более сложные выражения, определяющие данные, по которым выполняется группирование. Сложные выражения могут включать ссылки на несколько полей или параметров, условные инструкции или пользовательский код. При определении группы для области данных эти выражения добавляются к свойству **Группировать** . Дополнительные сведения см. в разделе [Добавление или удаление группы в области данных (построитель отчетов и службы SSRS)](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
 Чтобы выполнить слияние двух или нескольких групп, основанных на простых выражениях поля, добавьте каждое поле к списку выражений группы в определении группы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a>Примеры выражений группы  
 В следующей таблице приведены примеры выражений группы, которые можно использовать для определения группы.  
  
|Описание|Выражение|  
|-----------------|----------------|  
|Группирование по полю `Region` .|`=Fields!Region.Value`|  
|Группирование по фамилии и имени.|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|Группирование по первой букве фамилии.|`=Fields!LastName.Value.Substring(0,1)`|  
|Группирование по параметру, основанному на выборе пользователя.<br /><br /> В этом примере параметр `GroupBy` должен быть основан на списке допустимых значений, которые предоставляет допустимый вариант выбора для группирования.|`=Fields(Parameters!GroupBy.Value).Value`|  
|Группирование по трем отдельным возрастным диапазонам:<br /><br /> до 20, между 21 и 50, старше 50.|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|Группирование по многим возрастным диапазонам. В этом примере показан пользовательский код, написанный на языке [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, который возвращает строку, относящуюся к одному из следующих диапазонов:<br /><br /> от 25 и младше,<br /><br /> от 26 до 50;<br /><br /> от 51 до 75;<br /><br /> старше 75.|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> Пользовательский код:<br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a>См. также  
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
