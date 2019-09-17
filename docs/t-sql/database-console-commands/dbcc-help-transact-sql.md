---
title: DBCC HELP (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC HELP
- DBCC_HELP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC statement syntax information
- DBCC HELP statement
ms.assetid: 306092c6-4354-4e47-928b-606124fbdc6e
author: pmasl
ms.author: umajay
ms.openlocfilehash: a2b4899d3485af4a499c5018a8889a6ec37bbbbb
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211387"
---
# <a name="dbcc-help-transact-sql"></a>DBCC HELP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

Возвращает сведения о синтаксисе для определенной команды DBCC.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC HELP ( 'dbcc_statement' | @dbcc_statement_var | '?' )  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *dbcc_statement* | *@dbcc_statement_var*  
 Имя команды DBCC, для которой необходимо получить сведения о синтаксисе. Указывайте только часть команды DBCC, следующей за DBCC, например CHECKDB вместо DBCC CHECKDB.  
  
 ?  
 Возвращает все команды DBCC, для которых доступна справка.  
  
 WITH NO_INFOMSGS  
 Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="result-sets"></a>Результирующие наборы  
DBCC HELP возвращает результирующий набор, выводящий на экран синтаксис для определенной команды DBCC.
  
## <a name="permissions"></a>Разрешения  
Необходимо членство в предопределенной роли сервера **sysadmin** .
  
## <a name="examples"></a>Примеры  
### <a name="a-using-dbcc-help-with-a-variable"></a>A. Использование DBCC HELP с переменной  
Следующий пример возвращает сведения о синтаксисе DBCC `CHECKDB`.
  
```sql  
DECLARE @dbcc_stmt sysname;  
SET @dbcc_stmt = 'CHECKDB';  
DBCC HELP (@dbcc_stmt);  
GO  
```  
  
### <a name="b-using-dbcc-help-with-the--option"></a>Б. Использование DBCC HELP с ? Параметр  
Следующий пример возвращает все инструкции DBCC, для которых доступна справка.
  
```sql  
DBCC HELP ('?');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
