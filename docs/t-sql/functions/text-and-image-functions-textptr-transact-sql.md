---
title: TEXTPTR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dfca4f9367a15cf5c418b8d671ae968260323898
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948492"
---
# <a name="text-and-image-functions---textptr-transact-sql"></a>Функции для работы с изображениями и текстом — TEXTPTR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение текстового указателя, соответствующего столбцу **text**, **ntext** или **image**, в формате **varbinary**. Извлеченное значение указателя текста может быть использовано в инструкциях READTEXT, WRITETEXT и UPDATETEXT.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Дополнительные возможности недоступны.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TEXTPTR ( column )  
```  
  
## <a name="arguments"></a>Аргументы  
 *column*  
 Столбец типа **text**, **ntext** или **image**, который будет использоваться.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **varbinary**  
  
## <a name="remarks"></a>Remarks  
 Для таблиц с внутристрочным текстом функция TEXTPTR возвращает указатель для обрабатываемого текста. Можно получить правильный указатель на текст даже в том случае, если значение текста NULL.  
  
 Нельзя использовать функцию TEXTPTR для столбцов представлений. Она может быть использована только для столбцов таблицы. Чтобы использовать функцию TEXTPTR для столбца представления, необходимо установить уровень совместимости равным 80 с помощью инструкции [ALTER DATABASE Compatibility Level](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md). Если таблица не содержит в строке текстовых данных и если столбец типа **text**, **ntext** или **image** не был инициализирован с помощью инструкции UPDATETEXT, TEXTPTR возвращает указатель со значением NULL.  
  
 Используйте TEXTVALID, чтобы проверить, существует ли указатель на текст. Нельзя использовать инструкции UPDATETEXT, WRITETEXT или READTEXT без действительных текстовых указателей.  
  
 Приведенные ниже функции и инструкции также будут полезны при работе с данными типов **text**, **ntext** и **image**.  
  
|Функция или инструкция|Описание|  
|---------------------------|-----------------|  
|PATINDEX<b>('</b> _%pattern%_ **' ,** _expression_ **)**|Возвращает позицию символа указанной символьной строки в столбцах **text** или **ntext**.|  
|DATALENGTH<b>(</b>_expression_ **)**|Возвращает длину данных в столбцах **text**, **ntext** и **image**.|  
|SET TEXTSIZE|Возвращает предельный размер (в байтах) для данных типа **text**, **ntext** или **image**, возвращаемых инструкцией SELECT.|  
|SUBSTRING<b>(</b>_text_column_, _start_, _length_ **)**|Возвращает строку типа **varchar**, указанную с помощью определенного смещения *start* и длины *length*. Длина должна быть меньше 8 KБ.|  
  
## <a name="examples"></a>Примеры  
  
> [!NOTE]  
>  Для выполнения приведенных ниже примеров необходимо установить базу данных **pubs**.  
  
### <a name="a-using-textptr"></a>A. Использование TEXTPTR  
 На приведенном ниже примере показано, как использовать функцию `TEXTPTR` для нахождения столбца **image** `logo`, связанного с `New Moon Books`, в таблице `pub_info` базы данных `pubs`. Указатель на текст заносится в локальную переменную `@ptrval.`  
  
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
 На приведенном ниже примере показано, как обнаружить столбец `text` (`pr_info`), связанный с `pub_id``0736`, в таблице `pub_info` базы данных `pubs`. Сначала объявляется локальная переменная `@val`. После этого указатель на текст (длинная двоичная строка) записывается в `@val` и передается в качестве параметра в инструкцию `READTEXT`. Тем самым возвращается 10 байт, начиная с пятого (сдвиг равен 4).  
  
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
 [DATALENGTH (Transact-SQL)](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX (Transact-SQL)](../../t-sql/functions/patindex-transact-sql.md)   
 [READTEXT (Transact-SQL)](../../t-sql/queries/readtext-transact-sql.md)   
 [SET TEXTSIZE (Transact-SQL)](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Функции для работы с изображениями и текстом (Transact-SQL)](https://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  
