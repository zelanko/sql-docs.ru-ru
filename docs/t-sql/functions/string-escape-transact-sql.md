---
title: "STRING_ESCAPE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 41f969e292eff76c9a836ccd3177519d88e355ac
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Экранирует специальные символы в текстах и возвращает текст с escape-символов. **STRING_ESCAPE** — это детерминированная функция.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>Аргументы  
 *text*  
 — **Nvarchar**[выражение](../../t-sql/language-elements/expressions-transact-sql.md) выражение, представляющее объект, который следует экранировать.  
  
 *type*  
 Экранирование правила, которые будут применяться. В настоящее время является значение, поддерживаемое `'json'`.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar(max)** текст с escape-специальные и управляющие символы. В настоящее время **STRING_ESCAPE** только можно экранировать специальные символы JSON, показано в следующих таблицах.  
  
|Специальный символ|Закодированная последовательность|  
|-----------------------|----------------------|  
|Кавычки («»)|\\"|  
|обратный солидус (\\)|\\\|  
|солидус (/)|\\/|  
|Отмена|\b|  
|Подача страницы|\f|  
|Новая строка|\n|  
|Возврат каретки|\r|  
|Горизонтальная табуляция|\t|  
  
|Управляющий символ|Закодированная последовательность|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="examples"></a>Примеры  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Escape-текста в соответствии с правилами форматирования JSON  
 В следующем запросе экранирует специальные символы, используя правила JSON и возвращает escape-текста.  
  
```  
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>Б. Формат JSON-объект  
 Следующий запрос создает из переменных число и строка текста JSON и экранирует специальных символов JSON в переменных.  
  
```  
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',   
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>См. также:  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [ПОДСТРОКА &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
  
  

