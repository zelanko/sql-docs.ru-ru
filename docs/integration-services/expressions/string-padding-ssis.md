---
title: "Дополнение строк (службы SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "дополнение строк [службы Integration Services]"
  - "выражения [службы Integration Services], заполнение строк"
  - "дополнение строк"
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Дополнение строк (службы SSIS)
  Средство оценки выражений не проверяет, содержит ли строка начальные и конечные пробелы, и не приводит строки к одинаковой длине перед их сравнением. Если выражения требуют дополнения строк, можно использовать оператор + для сцепления значений столбцов и пустых строк. Дополнительные сведения см. в разделе [+ (объединение) (выражение SSIS)](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 С другой стороны, если надо удалить лишние пробелы, средство оценки выражений предоставляет функции LTRIM, RTRIM и TRIM, которые удаляют начальные либо конечные пробелы, либо и те и другие. Дополнительные сведения см. в разделах [LTRIM (выражение служб SSIS)](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM (выражение служб SSIS)](../../integration-services/expressions/rtrim-ssis-expression.md) и [TRIM (выражение служб SSIS)](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  Функция LEN включает в счет начальные и завершающие пробелы.  
  
## См. также  
 Техническая статья [Памятка выражений служб SSIS](http://go.microsoft.com/fwlink/?LinkId=746575)на сайте pragmaticworks.com  
  
  