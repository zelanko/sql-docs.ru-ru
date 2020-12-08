---
description: Как FOR JSON экранирует специальные и управляющие символы (SQL Server)
title: Как FOR JSON экранирует специальные и управляющие символы
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d7a99590fc36d246f19dbee3ebc227cfa10052d2
ms.sourcegitcommit: 28fecbf61ae7b53405ca378e2f5f90badb1a296a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96595195"
---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Как FOR JSON экранирует специальные и управляющие символы (SQL Server)

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sqlserver2016-asdb.md)]

  В этом разделе описано, как предложение **FOR JSON** в инструкции SQL Server **SELECT** экранирует специальные символы и представляет управляющие символы в выходных данных JSON.  

> [!IMPORTANT]
> На этой странице описывается встроенная поддержка JSON в Microsoft SQL Server. Общие сведения об экранировании и кодировании в формате JSON см. в статье 2.5 RFC по JSON ([https://www.ietf.org/rfc/rfc4627.txt](https://www.ietf.org/rfc/rfc4627.txt)).

## <a name="escaping-of-special-characters"></a>Экранирование специальных символов  
Если исходные данные содержат специальные символы, предложение **FOR JSON** экранирует их в выходных данных JSON с помощью `\`, как показано в следующей таблице. Такое экранирование происходит как в именах свойств, так и в их значениях.  
  
|**Специальный символ**|**Экранированные выходные данные**|  
|---------------------------|--------------------------|  
|Кавычки («»)|\\"|  
|Обратная косая черта (\\)|\\\\|  
|Косая черта (/)|\\/|  
|Отмена|\b|  
|Перевод страницы|\f|  
|Новая строка|\n|  
|Возврат каретки|\r|  
|Горизонтальная табуляция|\t|  
  
## <a name="control-characters"></a>Управляющие символы  
Если исходные данные содержат управляющие символы, предложение **FOR JSON** кодирует их в выходных данных JSON в формате `\u<code>`, как показано в следующей таблице.  
  
|**Управляющий символ**|**Закодированные выходные данные**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="example"></a>Пример  
 Ниже приведен пример выходных данных, возвращаемых **FOR JSON** для источника данных, содержащего как специальные символы, так и управляющие символы.  
  
 Запрос:  
  
```sql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Результат:  
  
```json  
{
    "KEY\\\t\/\"": "VALUE\\\t\/\r\n\"",
    "0": "\u0000",
    "1": "\u0001",
    "31": "\u001f"
}
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Дополнительные сведения о JSON в SQL Server и базе данных SQL Azure  
  
### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Предложение FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
