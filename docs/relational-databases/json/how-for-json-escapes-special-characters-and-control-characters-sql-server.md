---
title: "Как FOR JSON экранирует специальные и управляющие символы (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7f427b0fbdd91760d3c66f370c1bfa0b09b50f42
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Как FOR JSON экранирует специальные и управляющие символы (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Дополнительные сведения о встроенной поддержке JSON в SQL Server  
Большое количество решений, варианты использования и рекомендации см. в [записях Йована Поповича (Jovan Popovic), руководителя программы Майкрософт, в блогах о встроенной поддержке JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) в SQL Server и базах данных SQL Azure.
  
## <a name="see-also"></a>См. также:  
 [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Предложение FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
