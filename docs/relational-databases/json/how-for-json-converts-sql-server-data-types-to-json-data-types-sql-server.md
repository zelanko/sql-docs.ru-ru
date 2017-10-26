---
title: "Как SQL Server преобразует типы данных в формат JSON с помощью предложения FOR JSON (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: d866cc385b2c44d4594f4d4f8249df6f84ac48f2
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>Преобразование типов данных SQL Server в формат JSON с помощью предложения FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Предложение **FOR JSON** использует приведенные здесь правила для преобразования типов данных SQL в JSON в выходных данных JSON.  
  
|Категория|Тип данных SQL Server|Тип данных JSON|  
|--------------|--------------|---------------|  
|Знаковые и строковые типы|char, nchar, varchar, nvarchar|строка|  
|Числовые типы|int, bigint, float, decimal, numeric|number|  
|Битовый тип|bit|Логическое значение (true или false)|  
|Типы даты и времени|date, datetime, datetime2, time, datetimeoffset|строка|  
|Двоичные типы|varbinary, binary, image, timestamp, rowversion|Строка в кодировке Base64|  
|Типы CLR|geometry, geography, другие типы CLR|Не поддерживается. При их использовании возвращается ошибка.<br /><br /> В инструкции SELECT для преобразования исходных данных в тип данных SQL Server, который можно конвертировать в тип JSON, используйте CAST или CONVERT либо свойство или метод CLR. Например, для любого типа CLR используйте **ToString()**, а для типа geometry — **STAsText()**. Тип выходного значения JSON определяется типом данных, полученным после конвертации, которая была выполнена согласно инструкции SELECT.|  
|Другие типы|uniqueidentifier, money|строка|  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Много определенных решений, варианты использования и рекомендации см. в [записях блога о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) (категории SQL Server и Azure SQL Database (База данных SQL Azure), автор — руководитель программ корпорации Майкрософт Йован Попович (Jovan Popovic)).
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

