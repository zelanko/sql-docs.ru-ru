---
title: CURRENT_TIMEZONE_ID (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/18/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE)ID
- CURRENT_TIMEZONE_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone id [SQL Server]
- current timezoneid [SQL Server]
- system time zone id[SQL Server]
- system timezone id[SQL Server]
- functions [SQL Server], time zone id
- functions [SQL Server], timezoneid
- timezoneid [SQL Server], functions
- time zone id [SQL Server], functions
- CURRENT_TIMEZONE_ID function [SQL Server]
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: beaa58fddd6889b4ebbbce620d98277468dd67a2
ms.sourcegitcommit: 822d4b3cfa53269535500a3db5877a82b5076728
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87988839"
---
# <a name="current_timezone_id-transact-sql"></a>CURRENT_TIMEZONE_ID (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Эта функция возвращает идентификатор часового пояса, отслеживаемого сервером или экземпляром. Для Управляемого экземпляра SQL Azure возвращаемое значение зависит от часового пояса, автоматически назначенного экземпляру во время его создания, а не часового пояса базовой операционной системы.
  
> [!NOTE]  
> Для Базы данных SQL часовой пояс всегда устанавливается в формате UTC, а `CURRENT_TIMEZONE_ID` возвращает идентификатор часового пояса UTC.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CURRENT_TIMEZONE_ID ( )  
```
  
## <a name="arguments"></a>Аргументы

Эта функция не имеет аргументов.
  
## <a name="return-type"></a>Тип возвращаемых данных  

**varchar**
  
## <a name="remarks"></a>Remarks  

`CURRENT_TIMEZONE_ID` является недетерминированной функцией. Невозможно проиндексировать представления и выражения, ссылающиеся на этот столбец.
  
## <a name="example"></a>Пример

Возвращаемое значение будет отражать фактические часовой пояс и языковые параметры сервера или экземпляра.

```sql
SELECT CURRENT_TIMEZONE_ID();  
/* Returned:  
W. Europe Standard Time
*/
```  
  
## <a name="see-also"></a>См. также раздел

[Часовой пояс в Управляемом экземпляре SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone)

[CURRENT_TIMEZONE()](https://docs.microsoft.com/sql/t-sql/functions/current-timezone-transact-sql)
