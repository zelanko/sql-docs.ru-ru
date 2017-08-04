---
title: "Заполнение (службы SSIS) строк | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2cf3de41a65e975c99c68d459c804f1195fa4cd7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="string-padding-ssis"></a>Дополнение строк (службы SSIS)
  Средство оценки выражений не проверяет, содержит ли строка начальные и конечные пробелы, и не приводит строки к одинаковой длине перед их сравнением. Если выражения требуют дополнения строк, можно использовать оператор + для сцепления значений столбцов и пустых строк. Дополнительные сведения см. в разделе [+ (объединение) (выражение SSIS)](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 С другой стороны, если надо удалить лишние пробелы, средство оценки выражений предоставляет функции LTRIM, RTRIM и TRIM, которые удаляют начальные либо конечные пробелы, либо и те и другие. Дополнительные сведения см. в разделах [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM (выражение служб SSIS)](../../integration-services/expressions/rtrim-ssis-expression.md) и [TRIM (выражение служб SSIS)](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  Функция LEN включает в счет начальные и завершающие пробелы.  
  
## <a name="related-content"></a>См. также  
 Техническая статья [Памятка выражений служб SSIS](http://go.microsoft.com/fwlink/?LinkId=746575)на сайте pragmaticworks.com  
  
  
