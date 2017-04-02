---
title: "Преобразование типов данных SQL Server в формат JSON с помощью предложения FOR JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, преобразование типов данных"
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Преобразование типов данных SQL Server в формат JSON с помощью предложения FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Предложение **FOR JSON** использует приведенные здесь правила для преобразования типов данных SQL в JSON в выходных данных JSON.  
  
|Категория|Тип данных SQL Server|Тип данных JSON|  
|--------------|--------------|---------------|  
|Знаковые и строковые типы|(n)(var)(char)|строка|  
|Числовые типы|int, bigint, float, decimal, numeric|number|  
|Битовый тип|bit|Логическое значение (true или false)|  
|Типы даты и времени|date, datetime, datetime2, time, datetimeoffset|строка|  
|Двоичные типы|varbinary, binary, image, timestamp, rowversion|Строка в кодировке Base64|  
|Типы CLR|CLR, geometry, geography|Не поддерживается. При их использовании возвращается ошибка.<br /><br /> В инструкции SELECT для преобразования данных в тип данных, который можно конвертировать в тип JSON, используйте CAST или CONVERT либо свойство или метод CLR. Например, для любого типа CLR используйте **ToString()**, а для типа geometry — **STAsText()** . Тип выходного значения JSON определяется по типу данных, полученному после конвертации, которая была указана в инструкции SELECT.|  
|Другие типы|uniqueidentifier, money|строка|  
  
## См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  