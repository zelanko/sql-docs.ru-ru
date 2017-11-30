---
title: "Константы в выражениях (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a8c8fcb95cfc2134b04e77c0fb0fddf3464a706a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a>Константы в выражениях (построитель отчетов и службы SSRS)
  Константа состоит из литерального текста или предопределенного текста. Обработчик отчетов имеет доступ к стандартным константам, поэтому при включении их в выражения значения, которые они представляют, заменяются в выражении до его оценки.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a>Литеральный текст  
 В выражении литеральным текстом является текст, заключенный в двойные кавычки. Можно также ввести текст непосредственно в текстовое поле без двойных кавычек, если он не является частью выражения. Если значение текстового поля не начинается со знака равенства (=), текст рассматривается как литеральный. В следующей таблице показано несколько примеров литерального текста в выражении.  
  
|Константа|Отображение текста|Текст выражения|  
|--------------|------------------|---------------------|  
|Report run at:|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|Компания Adventure Works Cycles|Компания Adventure Works Cycles|Компания Adventure Works Cycles|  
|[Заключенный в скобки отображаемый текст]|\\[Заключенный в скобки отображаемый текст\\]|[Заключенный в скобки отображаемый текст]|  
  
## <a name="rdl-constants"></a>Константы языка определения отчетов  
 В выражении можно использовать константы, определенные в языке определения отчетов. В диалоговом окне **Выражение** константы появляются при создании выражения для свойства отчета, которое принимает только некоторые допустимые значения, известные также как перечислимые типы. В следующей таблице показаны два примера.  
  
|Свойство|Description|Значения|  
|--------------|-----------------|------------|  
|TextAlign|Допустимые значения для выравнивания текста в текстовом поле.|General, Left, Center, Right|  
|BorderStyle|Допустимые значения для линии, добавляемой в отчет.|Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot|  
  
## <a name="visual-basic-constants"></a>Константы языка Visual Basic  
 В выражении можно использовать константы, определенные в библиотеке времени выполнения [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Например, можно использовать константу **DateInterval.Day**. Следующее выражение возвращает число 10 для даты 10 января 2008 г.  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a>Константы среды CLR  
 В выражении можно использовать константы, определенные в классах среды CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . В следующей таблице показан пример определенного системой цвета.  
  
|Константа|Description|  
|--------------|-----------------|  
|MistyRose|При создании выражения для свойства отчета, основанного на цвете фона, можно указать цвет по имени. Допустимые имена перечислены в диалоговом окне **Выражение** .|  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно «Выражение»](http://msdn.microsoft.com/library/e6c74ccb-4594-4d4f-b958-618d710e34eb)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Диалоговое окно "Выражение" (построитель отчетов)](http://msdn.microsoft.com/library/e89c4d97-5d41-4b55-8695-79329edac15d)  
  
  
