---
title: Дополнение строк (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 27b200fd9f3d09fef0a94ea005add9bc7f1eca12
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156754"
---
# <a name="string-padding-ssis"></a>Дополнение строк (службы SSIS)
  Средство оценки выражений не проверяет, содержит ли строка начальные и конечные пробелы, и не приводит строки к одинаковой длине перед их сравнением. Если выражения требуют дополнения строк, можно использовать оператор + для сцепления значений столбцов и пустых строк. Дополнительные сведения см. в разделе [+ (объединение) (выражение SSIS)](concatenate-ssis-expression.md).  
  
 С другой стороны, если надо удалить лишние пробелы, средство оценки выражений предоставляет функции LTRIM, RTRIM и TRIM, которые удаляют начальные либо конечные пробелы, либо и те и другие. Дополнительные сведения см. в разделах [LTRIM (выражение служб SSIS)](trim-ssis-expression.md), [RTRIM (выражение служб SSIS)](rtrim-ssis-expression.md) и [TRIM (выражение служб SSIS)](trim-ssis-expression.md).  
  
> [!NOTE]  
>  Функция LEN включает в счет начальные и завершающие пробелы.  
  
## <a name="related-content"></a>См. также  
 Техническая статья [Памятка выражений служб SSIS](http://go.microsoft.com/fwlink/?LinkId=217683)на сайте pragmaticworks.com  
  
  
