---
title: "Инструкция UPDATE CUBE (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- UPDATE CUBE
- UPDATE_CUBE
- UPDATE
dev_langs: kbMDX
helpviewer_keywords:
- updating cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
ms.assetid: 6c8f23bb-401b-49de-843a-5324ac977239
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a5b55ccb969f2e4c7d18cdedab4c60f2ee13ef4b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-manipulation---update-cube"></a>Управление данными MDX - UPDATE CUBE
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Инструкция UPDATE CUBE используется для обратной записи данных в любую ячейку куба, которая суммируется с родительским элементом с помощью агрегатного выражения SUM. Дополнительные сведения и пример см. в разделе «Общие сведения о приложениях» в этой записи блога: [Создание приложения обратной записи со службами Analysis Services (блог)](http://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, возвращающее имя куба.  
  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
 *Новое_значение*  
 Допустимое числовое выражение.  
  
 *Weight_Expression*  
 Допустимое числовое многомерное выражение, возвращающее десятичное значение от 0 до 1.  
  
## <a name="remarks"></a>Замечания  
 Можно обновить значение указанной конечной или неконечной ячейки куба, по желанию размещая значение для указанной неконечной ячейки в зависимых конечных ячейках. Ячейка, указанная кортежным выражением, может представлять любую ячейку многомерного пространства (другими словами, ячейка необязательно должна быть конечной). Тем не менее, ячейки должны быть собраны с [сумма](../mdx/sum-mdx.md) агрегатной функции и не должны содержать вычисляемый элемент в кортеж, который используется для идентификации ячейки.  
  
 Может быть полезным подумать об **UPDATE CUBE** инструкцию как подпрограмму, которая автоматически создаст серию отдельных операций обратной записи в конечные и неконечные ячейки, сводимые в указанную сумму.  
  
 Ниже приведено описание методов выделения.  
  
 **USE_EQUAL_ALLOCATION:** каждой конечной ячейке, которая участвует в обновлении ячейки будет назначен одинаковые значения в соответствии со следующим выражением.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:**каждой конечной ячейке, которая участвует в обновлении ячейки изменяется в соответствии со следующего выражения.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:** каждой конечной ячейке, которая участвует в обновлении ячейки будет назначен равны значения в соответствии со следующим выражением.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:** каждой конечной ячейке, которая участвует в обновлении ячейки изменяется в соответствии со следующего выражения.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Если выражение веса не указано, **UPDATE CUBE** инструкции неявно использует следующее выражение.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Выражение веса должно быть отображено как десятичное значение от нуля (0) до 1. Оно определяет ту часть размещаемого значения, которую требуется присвоить конечным ячейкам, участвующим в размещении. Задачей программиста клиентского приложения является создание выражений, статистических значений, свертки которых будут равны размещаемому значению выражения.  
  
> [!CAUTION]  
>  Клиентское приложение должно выполнять размещение во всех измерениях параллельно, чтобы избежать возможных непредвиденных результатов, в том числе неправильных значений свертки или несогласованности данных.  
  
 Каждый **UPDATE CUBE** распределения считается неделимым в смысле транзакций. Это означает, что в случае сбоя при выполнении одной из операций размещения по какой-либо причине (например, вследствие ошибки в формуле или нарушения защиты), вся инструкция UPDATE CUBE завершается ошибкой. Перед обработкой вычислений отдельных операций размещения создается моментальный снимок данных, что обеспечивает правильность итоговых вычислений.  
  
> [!CAUTION]  
>  При использовании для меры, содержащей целые значения, метод USE_WEIGHTED_ALLOCATION может возвращать неточные результаты, что обусловлено округлениями при приращениях.  
  
> [!IMPORTANT]  
>  Если обновленные ячейки не пересекаются, свойство строки подключения **Update Isolation Level** может быть использовано для повышения производительности инструкции UPDATE CUBE.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Инструкции для манипулирования данными многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
