---
title: SET ANSI_DEFAULTS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET ANSI_DEFAULTS
- ANSI_DEFAULTS
- SET_ANSI_DEFAULTS_TSQL
- ANSI_DEFAULTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ANSI_DEFAULTS option
- SET ANSI_DEFAULTS statement
ms.assetid: bd721d97-6e23-488b-8c8c-c0453d5b3b86
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c343bc81ab744836db2a2e18ed3cd2890500d048
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="set-ansidefaults-transact-sql"></a>SET ANSI_DEFAULTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Управляет группой параметров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая задает определенное поведение стандарта ISO.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Синтаксис

```
-- Syntax for SQL Server

SET ANSI_DEFAULTS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_DEFAULTS ON
```

## <a name="remarks"></a>Remarks  
 SET ANSI_DEFAULTS является серверной настройкой, которая не изменяется клиентом. Клиент управляет собственными настройками. По умолчанию эти настройки противоположны настройкам сервера. Пользователи не могут изменять этот серверный параметр. Чтобы изменить поведение клиента, пользователи должны использовать SQL_COPT_SS_PRESERVE_CURSORS. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 При включении (ON) этого параметра включаются следующие параметры ISO.  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_NULL_DFLT_ON|SET IMPLICIT_TRANSACTIONS|  
|SET ANSI_PADDING|SET QUOTED_IDENTIFIER|  
|SET ANSI_WARNINGS||  
  
 В совокупности перечисленные параметры SET стандарта ISO определяют среду обработки запросов на все время сеанса пользователя, выполнения триггера или хранимой процедуры. Однако эти параметры SET не охватывают всех настроек, необходимых для полного соответствия стандарту ISO.  
  
 При работе с индексами для вычисляемых столбцов и индексированных представлений в значение ON должны быть установлены следующие четыре значения по умолчанию: ANSI_NULLS, ANSI_PADDING, ANSI_WARNINGS и QUOTED_IDENTIFIER. Кроме них при создании и изменении индексов для вычисляемых столбцов и индексированных представлений должны быть установлены следующие параметры SET:  ARITHABORT (ON), CONCAT_NULL_YIELDS_NULL (ON) и NUMERIC_ROUNDABORT (OFF). Дополнительные сведения о настройке параметров SET с индексированными представлениями и индексами на вычисляемых столбцах см. в подразделе "Рекомендации по использованию инструкций SET" раздела [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md).  
  
 При соединении с драйвером ODBC для Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или поставщика OLE DB для Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр ANSI_DEFAULTS автоматически устанавливается в значение ON. а CURSOR_CLOSE_ON_COMMIT и IMPLICIT_TRANSACTIONS значение OFF. Значение OFF для параметров SET CURSOR_CLOSE_ON_COMMIT и SET IMPLICIT_TRANSACTIONS можно указать в источнике данных ODBC, в атрибутах соединения ODBC или в свойствах соединения OLE DB, которые присваиваются в приложении перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. SET ANSI_DEFAULTS при соединении из приложений DB-Library имеет значение по умолчанию OFF.  
  
 При выполнении инструкции SET ANSI_DEFAULTS параметр SET QUOTED_IDENTIFIER устанавливается на стадии синтаксического анализа, а на стадии выполнения устанавливаются следующие параметры:  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET ANSI_WARNINGS|  
|SET ANSI_NULL_DFLT_ON|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_PADDING|SET IMPLICIT_TRANSACTIONS|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере устанавливается `SET ANSI_DEFAULTS ON` и выполняется инструкция `DBCC USEROPTIONS` для просмотра изменившихся параметров.  
  
```  
-- SET ANSI_DEFAULTS ON.  
SET ANSI_DEFAULTS ON;  
GO  
-- Display the current settings.  
DBCC USEROPTIONS;  
GO  
-- SET ANSI_DEFAULTS OFF.  
SET ANSI_DEFAULTS OFF;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [DBCC USEROPTIONS (Transact-SQL)](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON (Transact-SQL)](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)   
 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS (Transact-SQL)](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL)](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)   
 [SET IMPLICIT_TRANSACTIONS (Transact-SQL)](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  
