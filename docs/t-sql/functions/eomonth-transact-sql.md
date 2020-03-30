---
title: EOMONTH (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EOMONTH
- EOMONTH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EOMONTH function
ms.assetid: 1d060d8e-3297-4244-afef-57df2f8f92e2
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 481faddf2a0a12bcc44a8b4e677101afa68c37a4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67904378"
---
# <a name="eomonth-transact-sql"></a>EOMONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Эта функция возвращает последний день месяца, содержащего указанную дату, с необязательным смещением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
EOMONTH ( start_date [, month_to_add ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*start_date*  
Выражение даты, задающее дату, для которой необходимо возвратить последний день месяца.  
  
*month_to_add*  
Необязательное целочисленное выражение, задающее количество месяцев, добавляемых к параметру *start_date*.  
  
Если аргумент *month_to_add* имеет значение, то `EOMONTH` добавляет указанное число месяцев к значению *start_date* и возвращает последний день месяца, соответствующего полученной дате. Если при таком сложении происходит выход за пределы допустимого диапазона дат, функция `EOMONTH` вызывает ошибку.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **date**  
  
## <a name="remarks"></a>Remarks  
Функция `EOMONTH` поддерживает удаленное взаимодействие с серверами [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий. Она не может быть удаленной для серверов с версией ниже [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-eomonth-with-explicit-datetime-type"></a>A. EOMONTH с явным типом datetime  
  
```  
DECLARE @date DATETIME = '12/1/2011';  
SELECT EOMONTH ( @date ) AS Result;  
GO  
```  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
2011-12-31  
  
(1 row(s) affected)  
```  

### <a name="b-eomonth-with-string-parameter-and-implicit-conversion"></a>Б. EOMONTH со строковым параметром и неявным преобразованием  
  
```  
DECLARE @date VARCHAR(255) = '12/1/2011';  
SELECT EOMONTH ( @date ) AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
2011-12-31  
  
(1 row(s) affected)  
```  
  
### <a name="c-eomonth-with-and-without-the-month_to_add-parameter"></a>В. Функция EOMONTH с параметром month_to_add и без него  
  
Примечание. Значения в этих результирующих наборах отражают дату выполнения в следующем диапазоне (включительно):
        
        12/01/2011
        
        and
        
        12/31/2011

```sql  
DECLARE @date DATETIME = GETDATE();  
SELECT EOMONTH ( @date ) AS 'This Month';  
SELECT EOMONTH ( @date, 1 ) AS 'Next Month';  
SELECT EOMONTH ( @date, -1 ) AS 'Last Month';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
This Month  
-----------------------  
2011-12-31  
  
(1 row(s) affected)  
  
Next Month  
-----------------------  
2012-01-31  
  
(1 row(s) affected)  
  
Last Month  
-----------------------  
2011-11-30  
  
(1 row(s) affected)  
```  
  
  

