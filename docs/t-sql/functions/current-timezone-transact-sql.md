---
title: CURRENT_TIMEZONE (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/09/2019
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
ms.openlocfilehash: 6c29cfba3f47506cb88860763d6650cfb3ecab7f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026390"
---
# <a name="currenttimezone-transact-sql"></a>CURRENT_TIMEZONE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Эта функция возвращает имя часового пояса, отслеживаемого сервером или экземпляром. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`CURRENT_TIMEZONE` возвращаемое значение наследуется от операционной системы компьютера, на котором работает экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для Управляемого экземпляра базы данных SQL возвращаемое значение зависит от часового пояса, автоматически назначенного экземпляру во время его создания, а не часового пояса базовой операционной системы.
  
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
