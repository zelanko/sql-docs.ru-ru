---
title: "Функция TEXTPTR (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTPTR_TSQL
- TEXTPTR
dev_langs:
- TSQL
helpviewer_keywords:
- TEXTPTR function
- viewing text pointer values
- text-pointer values
- displaying text pointer values
ms.assetid: 2672b8cb-f747-46f3-9358-9b49b3583b8e
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 84eaad80eff48689f91ab2679611d6eab6b2ce4d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textptr-transact-sql"></a>Текст и изображения функции - TEXTPTR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает указатель на текст значение, соответствующее **текст**, **ntext**, или **изображения** столбца в **varbinary** формат. Извлеченное значение указателя текста может быть использовано в инструкциях READTEXT, WRITETEXT и UPDATETEXT.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Дополнительные возможности недоступны.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TEXTPTR ( column )  
```  
  
## <a name="arguments"></a>Аргументы  
 *столбец*  
 — **Текст**, **ntext**, или **изображения** столбец, который будет использоваться.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **varbinary**  
  
## <a name="remarks"></a>Замечания  
 Для таблиц с внутристрочным текстом функция TEXTPTR возвращает указатель для обрабатываемого текста. Можно получить правильный указатель на текст даже в том случае, если значение текста NULL.  
  
 Нельзя использовать функцию TEXTPTR для столбцов представлений. Она может быть использована только для столбцов таблицы. Чтобы использовать функцию TEXTPTR для столбца представления, необходимо установить уровень совместимости 80 с использованием [уровень совместимости инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md). Если таблица не содержит текста в строке, а **текст**, **ntext**, или **изображения** столбец не был инициализирован при помощи инструкции UPDATETEXT, TEXTPTR возвращает указатель null.  
  
 Используйте TEXTVALID, чтобы проверить, существует ли указатель на текст. Нельзя использовать инструкции UPDATETEXT, WRITETEXT или READTEXT без действительных текстовых указателей.  
  
 Эти функции и инструкции также полезны при работе с **текст**, **ntext**, и **изображения** данные.  
  
|Функция или инструкция|Description|  
|---------------------------|-----------------|  
|Функция PATINDEX**("***шаблон %***",** *выражение***)**|Возвращает позицию знака указанной символьной строки в **текст** или **ntext** столбцов.|  
|DATALENGTH**(***выражение***)**|Возвращает длину данных в **текст**, **ntext**, и **изображения** столбцов.|  
|SET TEXTSIZE|Возвращает предельный размер в байтах, **текст**, **ntext**, или **изображения** данные, возвращаемые инструкцией SELECT.|  
|Подстрока**(***text_column*, *запустить*, *длина***)**|Возвращает **varchar** строку, указанную при помощи заданного *запустить* смещение и *длина*. Длина должна быть меньше 8 KБ.|  
  
## <a name="examples"></a>Примеры  
  
> [!NOTE]  
>  Для выполнения следующих примеров необходимо установить **pubs** базы данных.  
  
### <a name="a-using-textptr"></a>A. Использование TEXTPTR  
 В следующем примере используется `TEXTPTR` функции, чтобы найти **изображения** столбца `logo` связанных с `New Moon Books` в `pub_info` таблицу `pubs` базы данных. Указатель на текст заносится в локальную переменную `@ptrval.`  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(logo)  
FROM pub_info pr, publishers p  
WHERE p.pub_id = pr.pub_id   
   AND p.pub_name = 'New Moon Books';  
GO  
```  
  
### <a name="b-using-textptr-with-in-row-text"></a>Б. Использование TEXTPTR с внутрирядным текстом  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указатель на внутрирядный текст должен использоваться внутри транзакции, как показано в примере.  
  
```  
CREATE TABLE t1 (c1 int, c2 text);  
EXEC sp_tableoption 't1', 'text in row', 'on';  
INSERT t1 VALUES ('1', 'This is text.');  
GO  
BEGIN TRAN;  
   DECLARE @ptrval VARBINARY(16);  
   SELECT @ptrval = TEXTPTR(c2)  
   FROM t1  
   WHERE c1 = 1;  
   READTEXT t1.c2 @ptrval 0 1;  
COMMIT;  
```  
  
### <a name="c-returning-text-data"></a>В. Возвращение текстовых данных  
 На следующем примере показано, как выбрать столбец `pub_id` и указатель на 16-байтовый текст столбца `pr_info` column из таблицы `pub_info`.  
  
```  
USE pubs;  
GO  
SELECT pub_id, TEXTPTR(pr_info)  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id                                      
------ ----------------------------------   
0736   0x6c0000000000feffb801000001000100   
0877   0x6d0000000000feffb801000001000300   
1389   0x6e0000000000feffb801000001000500   
1622   0x700000000000feffb801000001000900   
1756   0x710000000000feffb801000001000b00   
9901   0x720000000000feffb801000001000d00   
9952   0x6f0000000000feffb801000001000700   
9999   0x730000000000feffb801000001000f00   
  
(8 row(s) affected)  
```  
  
 На следующем примере показано, как вернуть первые `8000` байт текста, не используя TEXTPTR.  
  
```  
USE pubs;  
GO  
SET TEXTSIZE 8000;  
SELECT pub_id, pr_info  
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id pr_info                                                                                                                                                                                                                                                           
------ -----------------------------------------------------------------  
0736   New Moon Books (NMB) has just released another top ten publication. With the latest publication this makes NMB the hottest new publisher of the year!                                                                                                             
0877   This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washington, D.C.  
  
This is sample text data for Binnet & Hardley, publisher 0877 in the pubs database. Binnet & Hardley is located in Washi   
1389   This is sample text data for Algodata Infosystems, publisher 1389 in the pubs database. Algodata Infosystems is located in Berkeley, California.  
  
9999   This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in Paris, France.  
  
This is sample text data for Lucerne Publishing, publisher 9999 in the pubs database. Lucerne publishing is located in   
  
(8 row(s) affected)  
```  
  
### <a name="d-returning-specific-text-data"></a>Г. Возвращение заданных текстовых данных  
 Следующий пример находит `text` столбца (`pr_info`) связанный с `pub_id``0736` в `pub_info` таблицу `pubs` базы данных. Сначала объявляется локальная переменная `@val`. После этого указатель на текст (длинная двоичная строка) записывается в `@val` и передается в качестве параметра в инструкцию `READTEXT`. Тем самым возвращается 10 байт, начиная с пятого (сдвиг равен 4).  
  
```  
USE pubs;  
GO  
DECLARE @val varbinary(16);  
SELECT @val = TEXTPTR(pr_info)   
FROM pub_info  
WHERE pub_id = '0736';  
READTEXT pub_info.pr_info @val 4 10;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pr_info                                                                                                                                                                                                                                                           
-----------------------------------------------------------------------  
 is sample  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:  
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [READTEXT &#40; Transact-SQL &#41;](../../t-sql/queries/readtext-transact-sql.md)   
 [Значение TEXTSIZE &#40; Transact-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Текст и изображения функции &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  

