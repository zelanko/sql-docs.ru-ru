---
title: Как FOR JSON экранирует специальные и управляющие символы (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: douglasl
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c3df2557120308cc77b0abbd3f9c3bc5eed73b36
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52542514"
---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Как FOR JSON экранирует специальные и управляющие символы (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В этом разделе описано, как предложение **FOR JSON** в инструкции SQL Server **SELECT** экранирует специальные символы и представляет управляющие символы в выходных данных JSON.  

> [!IMPORTANT]
> На этой странице описывается встроенная поддержка JSON в Microsoft SQL Server. Общие сведения об экранировании и кодировании в формате JSON см. в статье 2.5 RFC по JSON ([https://www.ietf.org/rfc/rfc4627.txt](https://www.ietf.org/rfc/rfc4627.txt)).

## <a name="escaping-of-special-characters"></a>Экранирование специальных символов  
Если исходные данные содержат специальные символы, предложение **FOR JSON** экранирует их в выходных данных JSON с помощью `\`, как показано в следующей таблице. Такое экранирование происходит как в именах свойств, так и в их значениях.  
  
|**Специальный символ**|**Экранированные выходные данные**|  
|---------------------------|--------------------------|  
|Кавычки («»)|\\"|  
|Обратная косая черта (\\)|\\\|  
|Косая черта (/)|\\/|  
|Отмена|\b|  
|Подача страницы|\f|  
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
  
### <a name="microsoft-blog-posts"></a>Публикации блога Майкрософт  
  
Конкретные решения, варианты использования и рекомендации см. в [записях блога](https://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) о встроенной поддержке JSON в SQL Server и базе данных SQL Azure.  

### <a name="microsoft-videos"></a>Видео Майкрософт

Наглядные инструкции по встроенной поддержке JSON в SQL Server и базе данных SQL Azure см. в следующих видео.

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 и поддержка JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Использование JSON в SQL Server 2016 и базе данных SQL Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON как мост между NoSQL и реляционными решениями)
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Предложение FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
