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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: f850839d54f5a1e4d58277524b1f2d35b56c7b4e
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
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
  
## <a name="remarks"></a>Remarks  
  
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
  
## <a name="see-also"></a>См. также  
 [CONCAT &#40; Transact-SQL &#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [Функция FORMATMESSAGE &#40; Transact-SQL &#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40; Transact-SQL &#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [Заменить &#40; Transact-SQL &#41;](../../t-sql/functions/replace-transact-sql.md)  
 [ОБРАТИТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STUFF &#40; Transact-SQL &#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [ПРЕОБРАЗОВАТЬ &#40; Transact-SQL &#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
