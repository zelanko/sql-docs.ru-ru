---
title: CURRENT_TIMEZONE (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/28/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TIMEZONE
- CURRENT_TIMEZONE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- current time zone [SQL Server]
- current timezone [SQL Server]
- system time zone [SQL Server]
- system timezone [SQL Server]
- functions [SQL Server], time zone
- functions [SQL Server], timezone
- timezone [SQL Server], functions
- time zone [SQL Server], functions
- CURRENT_TIMEZONE function [SQL Server]
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 760da1491a7fbf4633cb02fe1fea8568e7ab9fa1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85684493"
---
# <a name="current_timezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Эта функция возвращает имя часового пояса, отслеживаемого сервером или экземпляром. Для Управляемого экземпляра Базы данных SQL возвращаемое значение зависит от часового пояса, автоматически назначенного экземпляру во время его создания, а не часового пояса базовой операционной системы.
  
> [!NOTE]  
> Для отдельных баз данных SQL и баз данных SQL в составе пула часовой пояс всегда устанавливается в формате UTC и `CURRENT_TIMEZONE` возвращает имя часового пояса UTC.
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CURRENT_TIMEZONE ( )  
```
  
## <a name="arguments"></a>Аргументы

Эта функция не имеет аргументов.
  
## <a name="return-type"></a>Тип возвращаемых данных  

**varchar**
  
## <a name="remarks"></a>Remarks  

`CURRENT_TIMEZONE` является недетерминированной функцией. Невозможно проиндексировать представления и выражения, ссылающиеся на этот столбец.
  
## <a name="example"></a>Пример

Обратите внимание, что возвращаемое значение будет отражать фактические часовой пояс и языковые параметры сервера или экземпляра.

```sql
SELECT CURRENT_TIMEZONE();  
/* Returned:  
(UTC+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna 
*/
```  
  
## <a name="see-also"></a>См. также раздел

[SQL Database Managed Instance Time Zone](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-timezone) (Часовые пояса в Управляемом экземпляре Базы данных SQL)

[CURRENT_TIMEZONE_ID()](https://docs.microsoft.com/sql/t-sql/functions/current-timezone-id-transact-sql)
