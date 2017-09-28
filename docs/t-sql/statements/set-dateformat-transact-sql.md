---
title: "SET DATEFORMAT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFORMAT
- SET DATEFORMAT
- SET_DATEFORMAT_TSQL
- DATEFORMAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], formats
- dates [SQL Server], ordering date parts
- SET DATEFORMAT option [SQL Server]
- DATEFORMAT option [SQL Server]
- date and time [SQL Server], SET DATEFORMAT
- options [SQL Server], date
- date and time [SQL Server], DATEFORMAT
- dateparts [SQL Server], dateformat
ms.assetid: da217878-7ec4-477e-aa13-604073c948f8
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eba2bdb31a805c61b92a88ce5699c05dfa7fe09f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает порядок составляющих частей даты месяца, дня и года для интерпретации **даты**, **smalldatetime**, **datetime**, **datetime2** и **datetimeoffset** символьные строки.  
  
 Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>Аргументы  
 *формат* | **@***format_var*  
 Порядок следования составляющих частей даты. Допустимые параметры: **МДГ**, **ДМГ**, **гмд**, **ГДМ**, **МГД**, и **ДГМ**. Может быть задано в формате Юникод или в виде двухбайтовой кодировки (DBCS), преобразованной в Юникод. Для языкового стандарта «Английский По умолчанию Английский — **МДГ**. По умолчанию DATEFORMAT всех поддерживаемых языков см. в разделе [sp_helplanguage &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Параметра DATEFORMAT **ГДМ** не поддерживается для **даты**, **datetime2** и **datetimeoffset** типов данных.  
  
 Влияние параметра DATEFORMAT на интерпретацию символьных строк может быть разным для **datetime** и **smalldatetime** от значений **Дата**, **datetime2** и **datetimeoffset** значения в зависимости от строки формата. Эта настройка влияет на интерпретацию символьных строк при их преобразовании в значения даты для хранения в базе данных. Настройка не влияет на отображение дат, хранящихся в базе данных, а также на формат их хранения.  
  
 Некоторые форматы символьных строк, например ISO 8601, интерпретируются независимо от значения параметра DATEFORMAT.  
  
 Установка SET DATEFORMAT происходит во время выполнения, а не во время синтаксического анализа.  
  
 SET DATEFORMAT переопределяет неявное даты установкой формата [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере в качестве входных параметров сеансов используются различные строковые значения дат с одинаковым значением параметра `DATEFORMAT`.  
  
```  
-- Set date format to day/month/year.  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '31/12/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: 2008-12-31 09:01:01.123  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '12/31/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: Msg 241: Conversion failed when converting date and/or time -- from character string.  
  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```  
-- Set date format to month/day/year.  
SET DATEFORMAT mdy;  
DECLARE @datevar datetime2 = '12/31/2012 09:01:01.1234567';  
SELECT @datevar;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


