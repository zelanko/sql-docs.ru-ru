---
title: Как SQL Server преобразует типы данных в формат JSON с помощью предложения FOR JSON (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 07/07/2016
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7e59fa518c4682c77548cb5b408b4856e7096ed6
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56033205"
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>Преобразование типов данных SQL Server в формат JSON с помощью предложения FOR JSON (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
