---
title: "Функция ISDATE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISDATETIME
- ISDATE_TSQL
- ISDATE
- ISDATETIME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], ISDATE
- validate dates times [SQL Server]
- formats [SQL Server], time
- dates [SQL Server], validate
- verify dates times [SQL Server]
- functions [SQL Server], time
- formats [SQL Server], dates
- functions [SQL Server], date and time
- time [SQL Server], functions
- time [SQL Server], validate
- ISDATE function [SQL Server]
ms.assetid: 8e2c9ee7-388a-432f-b2c9-7b398f26bf85
caps.latest.revision: "54"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b9f17d829f3acf7c72a8599eb71b945c58d4cb0a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="isdate-transact-sql"></a>ISDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает 1, если *выражение* является допустимым **даты**, **время**, или **datetime** значение; в противном случае — 0.  
  
 Функция ISDATE возвращает 0, если *выражение* — **datetime2** значение.  
  
 Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md). Обратите внимание на то, что диапазоном для данных типа datetime являются значения от 1753-01-01 до 9999-12-31, в то время как диапазоном для данных даты являются значения от 0001-01-01 до 9999-12-31.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ISDATE ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Символьная строка или [выражение](../../t-sql/language-elements/expressions-transact-sql.md) , можно преобразовать в символьную строку. Выражение должно включать не более 4 000 символов. Типы данных даты и времени (за исключением типа datetime и smalldatetime), не разрешены к использованию в качестве аргумента функции ISDATE.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **int**  
  
## <a name="remarks"></a>Замечания  
 Функция ISDATE детерминирована, только в том случае, если используется совместно с [преобразовать](../../t-sql/functions/cast-and-convert-transact-sql.md) работать, если параметр стиля CONVERT задан и стиль не равен 0, 100, 9 или 109.  
  
 Возвращаемое значение ISDATE зависит от параметров, заданные [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md), [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) и [Настройка параметра конфигурации сервера язык по умолчанию](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md).  
  
## <a name="isdate-expression-formats"></a>Форматы выражения ISDATE  
 Примеры допустимых форматов, для которых функция ISDATE возвращает 1, см. в разделе «Поддерживаемые форматы строковых литералов для типа данных datetime» [datetime](../../t-sql/data-types/datetime-transact-sql.md) и [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) разделы. Дополнительные примеры см. также входной или выходной столбец «Аргументы» раздела [CAST и CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 В следующей таблице приводятся недопустимые форматы входных выражений, для которых возвращается 0 или ошибка.  
  
|ISDATE, выражение|Возвращенное значение ISDATE|  
|-----------------------|-------------------------|  
|NULL|0|  
|Значения типов данных, перечисленных в [типы данных](../../t-sql/data-types/data-types-transact-sql.md) в любой категории типов данных, кроме символьных строк, символьные строки в Юникоде, или дата и время.|0|  
|Значения **текст**, **ntext**, или **изображение** типов данных.|0|  
|Любое значение, имеющее более трех позиций долей секунды (от 0,0000 до 0,0000000...n) Функция ISDATE возвращает 0, если *выражение* — **datetime2** значение, но возвращает 1, если *выражение* является допустимым **datetime** значение.|0|  
|Любое значение, сочетающее допустимую дату с недопустимым значением, например 1995-10-1a.|0|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-isdate-to-test-for-a-valid-datetime-expression"></a>A. Использование функции ISDATE для проверки допустимого выражения datetime  
 Следующий пример показывает, как использовать `ISDATE` Чтобы проверить, является ли символьная строка допустимым **datetime**.  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    PRINT 'VALID'  
ELSE  
    PRINT 'INVALID';  
```  
  
### <a name="b-showing-the-effects-of-the-set-dateformat-and-set-language-settings-on-return-values"></a>Б. Влияние настроек SET DATEFORMAT и SET LANGUAGE на возвращаемые значения  
 Следующие инструкции возвращают значения, зависящие от настроек `SET DATEFORMAT` и `SET LANGUAGE`.  
  
```  
/* Use these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
/* Expression in mdy dateformat */  
SELECT ISDATE('04/15/2008'); --Returns 1.  
/* Expression in mdy dateformat */  
SELECT ISDATE('04-15-2008'); --Returns 1.   
/* Expression in mdy dateformat */  
SELECT ISDATE('04.15.2008'); --Returns 1.   
/* Expression in myd  dateformat */  
SELECT ISDATE('04/2008/15'); --Returns 1.  
  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET DATEFORMAT dmy;  
SELECT ISDATE('15/04/2008'); --Returns 1.  
SET DATEFORMAT dym;  
SELECT ISDATE('15/2008/04'); --Returns 1.  
SET DATEFORMAT ydm;  
SELECT ISDATE('2008/15/04'); --Returns 1.  
SET DATEFORMAT ymd;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET LANGUAGE English;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET LANGUAGE Hungarian;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET LANGUAGE Swedish;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET LANGUAGE Italian;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
/* Return to these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-isdate-to-test-for-a-valid-datetime-expression"></a>В. Использование функции ISDATE для проверки допустимого выражения datetime  
 Следующий пример показывает, как использовать `ISDATE` Чтобы проверить, является ли символьная строка допустимым **datetime**.  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    SELECT 'VALID';  
ELSE  
    SELECT 'INVALID';  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

