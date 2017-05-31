---
title: "Как FOR JSON экранирует специальные и управляющие символы (SQL Server) | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1b2a6a10c3aa3ec3caa432a208be4b3023072046
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Как FOR JSON экранирует специальные и управляющие символы (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В этом разделе описано, как предложение **FOR JSON** в инструкции SQL Server **SELECT** экранирует специальные символы и представляет управляющие символы в выходных данных JSON.  

> [!IMPORTANT]
> На этой странице описывается встроенная поддержка JSON в Microsoft SQL Server. Общие сведения об экранировании и кодировании в формате JSON см. в статье 2.5 RFC по JSON ([http://www.ietf.org/rfc/rfc4627.txt](http://www.ietf.org/rfc/rfc4627.txt)).

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
|…|…|  
|CHAR(31)|\u001f|  
  
## <a name="example"></a>Пример  
 Ниже приведен пример выходных данных, возвращаемых **FOR JSON** для источника данных, содержащего как специальные символы, так и управляющие символы.  
  
 Запрос:  
  
```tsql  
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
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Предложение FOR](../../t-sql/queries/select-for-clause-transact-sql.md)

