---
description: DBCC USEROPTIONS (Transact-SQL)
title: DBCC USEROPTIONS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC USEROPTIONS
- DBCC_USEROPTIONS_TSQL
- USEROPTIONS_TSQL
- USEROPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC USEROPTIONS statement
- active SET options
- SET statement, active SET options
ms.assetid: 565ab112-7af1-4c18-a579-07cdb332f539
author: pmasl
ms.author: umajay
ms.openlocfilehash: 0b5e147a87e6559d1d3bd2782d46bf09a783297a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417560"
---
# <a name="dbcc-useroptions-transact-sql"></a>DBCC USEROPTIONS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает число активных (установленных) параметров SET для текущего соединения.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC USEROPTIONS  
[ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
NO_INFOMSGS  
Подавляет все информационные сообщения со степенями серьезности от 0 до 10.
  
## <a name="result-sets"></a>Результирующие наборы  
Инструкция DBCC USEROPTIONS возвращает столбец с именем параметра SET и столбец с его значением (значения и записи могут быть разными):

```sql

Set Option                   Value`  
---------------------------- ---------------------------`  
textsize                     64512 
language                     us_english 
dateformat                   mdy  
datefirst                    7 
lock_timeout                 -1 
quoted_identifier            SET 
arithabort                   SET 
ansi_null_dflt_on            SET 
ansi_warnings                SET 
ansi_padding                 SET 
ansi_nulls                   SET 
concat_null_yields_null      SET 
isolation level              read committed  
(13 row(s) affected) 
DBCC execution completed. If DBCC printed error messages, contact your system administrator.
 ```  
  
## <a name="remarks"></a>Комментарии  
Инструкция DBCC USEROPTIONS сообщает об уровне изоляции «зафиксированная операция чтения моментального снимка», если параметр базы данных READ_COMMITTED_SNAPSHOT имеет значение ON, а уровню изоляции транзакции задано значение «зафиксированная операция чтения». Фактический уровень изоляции: зафиксированная операция чтения.
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом роли **public**.
  
## <a name="examples"></a>Примеры  
В следующем примере возвращаются активные параметры SET для текущего соединения.
  
```sql  
DBCC USEROPTIONS;  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
[SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
  
  
