---
title: "SUBSTRING (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUBSTRING
- SUBSTRING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- portion of expression returned [SQL Server]
- part of expression returned [SQL Server]
- SUBSTRING function
- offsets [SQL Server]
- binary [SQL Server], returning part of
- expressions [SQL Server], part returned
- characters [SQL Server], returning part of
ms.assetid: a19c808f-aaf9-4a69-af59-b1a5fc3e5c4c
caps.latest.revision: 65
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7f36ec82c65e5d52c2186c67033adddbf1700c4d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="substring-transact-sql"></a>SUBSTRING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает часть символьного, двоичного, текстового или графического выражения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SUBSTRING ( expression ,start , length )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — **Символ**, **двоичных**, **текст**, **ntext**, или **изображения**[выражение](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *Запуск*  
 Должно быть целым числом или **bigint** выражение, которое указывает, где начала возвращаемых символов. (Нумерация достигается, когда 1 на основе, что первый символ в выражении равен 1). Если *запустить* меньше 1, возвращаемое выражение начинается с первого символа, который указан в *выражение*. В этом случае количество возвращаемых символов является наибольшим значением либо суммы *запустить* + *длина*- 1 или 0. Если *запустить* больше, чем количество символов в выражении значения, возвращается выражение нулевой длины.  
  
 *length*  
 Положительное целое число или **bigint** выражение, которое указывает, сколько символов *выражение* будут возвращены. Если *длина* имеет отрицательное значение, выводится сообщение об ошибке и выполнение инструкции прервано. Если сумма *запустить* и *длина* больше, чем количество символов в *выражение*, всего значения выражения, начиная с *запустить*возвращается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает символьные данные, если *выражение* является одним из поддерживаемых символьных типов данных. Возвращает двоичные данные, если *выражение* является одним из поддерживаемых **двоичных** типов данных. Возвращенная строка имеет тот же самый тип, как и заданное выражение. Исключения указаны в таблице.  
  
|Заданное выражение|Возвращаемый тип|  
|--------------------------|-----------------|  
|**char**/**varchar**/**текста**|**varchar**|  
|**nchar**/**nvarchar**/**ntext**|**nvarchar**|  
|**двоичный**/**varbinary**/**изображения**|**varbinary**|  
  
## <a name="remarks"></a>Замечания  
 Значения для *запустить* и *длина* должен быть указан в символах для **ntext**, **char**, или **varchar**  и байтов для типов данных **текст**, **изображения**, **двоичных**, или **varbinary** типов данных.  
  
 *Выражение* должно быть **varchar(max)** или **varbinary(max)** при *запустить* или *длина* содержит значение размером более 2147483647.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Дополнительные символы (суррогатные пары)  
 При использовании параметров сортировки дополнительных символов (SC), оба *запустить* и *длина* обрабатывают каждую суррогатную пару *выражение* как один символ. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-substring-with-a-character-string"></a>A. Использование SUBSTRING с символьной строкой  
 Следующий пример показывает, как получить часть символьной строки. Из `sys.databases` таблицы, этот запрос возвращает система имена баз данных в первом столбце первой буквы базы данных в столбце второй и третий и четвертый символы в последнем столбце.  
  
```  
SELECT name, SUBSTRING(name, 1, 1) AS Initial ,
SUBSTRING(name, 3, 2) AS ThirdAndFourthCharacters
FROM sys.databases  
WHERE database_id < 5;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

|имя |Initial |ThirdAndFourthCharacters|
|---|--|--|
|master  |m  |ST |
|tempdb  |t  |пакет управления |
|model   |m  |de |
|msdb    |m  |DB |


  
 Далее показано, как можно вывести второй, третий и четвертый символ строковой константы `abcdef`.  
  
```  
SELECT x = SUBSTRING('abcdef', 2, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x  
----------  
bcd  
  
(1 row(s) affected)
```  
  
### <a name="b-using-substring-with-text-ntext-and-image-data"></a>Б. Использование SUBSTRING с данными типа text, ntext или image  
  
> [!NOTE]  
>  Для выполнения следующих примеров необходимо установить **pubs** базы данных.  
  
 Следующий пример показывает, как вернуть первые 10 символов из каждого из **текст** и **изображения** столбца данных в `pub_info` таблицу `pubs` базы данных. **текст** данные возвращаются в виде **varchar**, и **изображения** данные возвращаются в виде **varbinary**.  
  
```  
USE pubs;  
SELECT pub_id, SUBSTRING(logo, 1, 10) AS logo,   
   SUBSTRING(pr_info, 1, 10) AS pr_info  
FROM pub_info  
WHERE pub_id = '1756';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 pub_id logo    pr_info
------ ---------------------- ----------
1756   0x474946383961E3002500 This is sa

(1 row(s) affected)
```  
  
 В следующем примере показано влияние ПОДСТРОКИ на обоих **текст** и **ntext** данных. Во-первых, пример создает новую таблицу в базе данных `pubs` под именем `npub_info`. Во-вторых, пример создает столбец `pr_info` в таблице `npub_info` из первых 80 символов столбца `pub_info.pr_info` и добавляет `ü` в качестве первого символа. Наконец `INNER JOIN` получает все идентификационные номера издателей и `SUBSTRING` обоих **текст** и **ntext** сведениями об издателях.  
  
```  
IF EXISTS (SELECT table_name FROM INFORMATION_SCHEMA.TABLES   
      WHERE table_name = 'npub_info')  
   DROP TABLE npub_info;  
GO  
-- Create npub_info table in pubs database. Borrowed from instpubs.sql.  
USE pubs;  
GO  
CREATE TABLE npub_info  
(  
 pub_id char(4) NOT NULL  
    REFERENCES publishers(pub_id)  
    CONSTRAINT UPKCL_npubinfo PRIMARY KEY CLUSTERED,  
pr_info ntext NULL  
);  
  
GO  
  
-- Fill the pr_info column in npub_info with international data.  
RAISERROR('Now at the inserts to pub_info...',0,1);  
  
GO  
  
INSERT npub_info VALUES('0736', N'üThis is sample text data for New Moon Books, publisher 0736 in the pubs database')  
,('0877', N'üThis is sample text data for Binnet & Hardley, publisher 0877 in the pubs databa')  
,('1389', N'üThis is sample text data for Algodata Infosystems, publisher 1389 in the pubs da')  
,('9952', N'üThis is sample text data for Scootney Books, publisher 9952 in the pubs database')  
,('1622', N'üThis is sample text data for Five Lakes Publishing, publisher 1622 in the pubs d')  
,('1756', N'üThis is sample text data for Ramona Publishers, publisher 1756 in the pubs datab')  
,('9901', N'üThis is sample text data for GGG&G, publisher 9901 in the pubs database. GGG&G i')  
,('9999', N'üThis is sample text data for Lucerne Publishing, publisher 9999 in the pubs data');  
GO  
-- Join between npub_info and pub_info on pub_id.  
SELECT pr.pub_id, SUBSTRING(pr.pr_info, 1, 35) AS pr_info,  
   SUBSTRING(npr.pr_info, 1, 35) AS npr_info  
FROM pub_info pr INNER JOIN npub_info npr  
   ON pr.pub_id = npr.pub_id  
ORDER BY pr.pub_id ASC;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-substring-with-a-character-string"></a>В. Использование SUBSTRING с символьной строкой  
 Следующий пример показывает, как получить часть символьной строки. Из таблицы `dbo.DimEmployee` данный запрос возвращает фамилию в одном столбце и первую букву имени в другом.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUBSTRING(FirstName, 1, 1) AS Initial  
FROM dbo.DimEmployee  
WHERE LastName LIKE 'Bar%'  
ORDER BY LastName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName             Initial
-------------------- -------
Barbariol            A
Barber               D
Barreto de Mattos    P
```  
  
 Приведенный ниже показано, как вернуть второй, третий и четвертый символы строковой константы `abcdef`.  
  
```  
USE ssawPDW;  
  
SELECT TOP 1 SUBSTRING('abcdef', 2, 3) AS x FROM dbo.DimCustomer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x
-----
bcd
```  
  
## <a name="see-also"></a>См. также:  
 [Строковые функции &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



