---
title: STRING_ESCAPE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = azuresqldb-current||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: d845257313466caa21976feaf69598e404a03962
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906860"
---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Экранирует специальные символы в тексте и возвращает текст с экранированными символами. **STRING_ESCAPE** — это детерминированная функция.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>Аргументы

 *text*  
 Выражение **nvarchar**[expression](../../t-sql/language-elements/expressions-transact-sql.md), представляющее объект, который следует экранировать.  
  
 *type*  
 Правила экранирования, которые будут применены. В настоящее время поддерживается значение `'json'`.  
  
## <a name="return-types"></a>Типы возвращаемых данных

 Текст **nvarchar(max)** с экранированными специальными и управляющими символами. В настоящее время с помощью функции **STRING_ESCAPE** можно экранировать только специальные символы JSON, представленные в таблицах ниже.  
  
|Специальный символ|Закодированная последовательность|  
|-----------------------|----------------------|  
|Кавычки («»)|\\"|  
|Обратный солидус (\\)| \\\\ |  
|Солидус (/)|\\/|  
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
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Экранирование текста согласно правилам форматирования JSON

 Приведенный ниже запрос экранирует специальные символы с использованием правил JSON и возвращает экранированный текст.  
  
```sql
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>Б. Форматирование объекта JSON

 Приведенный ниже запрос создает текст в формате JSON на основе числовых и строковых переменных, а затем экранирует все специальные символы JSON в переменных.  
  
```
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>См. также:

 [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG (Transact-SQL)](../../t-sql/functions/string-agg-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE (Transact-SQL)](../../t-sql/functions/translate-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)
