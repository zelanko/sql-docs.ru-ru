---
title: SET DATEFORMAT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 7d0114bb98134b86b92bae634f2746abce163279
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456648"
---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает порядок частей даты (месяца, дня и года) для интерпретации символьных строк **date**, **smalldatetime**, **datetime**, **datetime2** и **datetimeoffset**.  
  
 Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>Аргументы  
 *format* | **@***format_var*  
 Порядок следования составляющих частей даты. Допустимые параметры: **mdy**, **dmy**, **ymd**, **ydm**, **myd** и **dym**. Может быть задано в формате Юникод или в виде двухбайтовой кодировки (DBCS), преобразованной в Юникод. Для языкового стандарта «Английский (США)" значение по умолчанию равно **mdy**. Значения параметра DATEFORMAT по умолчанию для всех поддерживаемых языков см. в разделе [sp_helplanguage (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Значение **ydm** параметра DATEFORMAT не поддерживается для типов данных **date**, **datetime2** и **datetimeoffset**.  
  
 Влияние параметра DATEFORMAT на интерпретацию символьных строк может отличаться для значений **datetime** и **smalldatetime** и значений **date**, **datetime2** и **datetimeoffset** в зависимости от формата строки. Эта настройка влияет на интерпретацию символьных строк при их преобразовании в значения даты для хранения в базе данных. Настройка не влияет на отображение дат, хранящихся в базе данных, а также на формат их хранения.  
  
 Некоторые форматы символьных строк, например ISO 8601, интерпретируются независимо от значения параметра DATEFORMAT.  
  
 Установка SET DATEFORMAT происходит во время выполнения, а не во время синтаксического анализа.  
  
 SET DATEFORMAT имеет преимущество над неявной установкой формата даты [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

