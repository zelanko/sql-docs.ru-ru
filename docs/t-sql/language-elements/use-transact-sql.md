---
title: "Использование (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 11/28/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USE_TSQL
- USE
dev_langs:
- TSQL
helpviewer_keywords:
- USE statement
- database context [SQL Server]
- context changes [SQL Server]
- modifying database context
ms.assetid: c05acac8-c063-4770-8e36-d7f71d500b10
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6274293bd4caedc9cad00ad4532952e63e3e989
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="use-transact-sql"></a>USE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Изменяет контекст базы данных на указанную базу данных или моментальный снимок базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
USE { database_name }   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных или моментального снимка базы данных, на который переключается контекст пользователя. Базы данных и имена моментальных снимков базы данных должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 В [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] параметр базы данных может ссылаться только на текущую базу данных. Если указан параметр базы данных, кроме текущей базы данных, `USE` инструкция не выполняет переключения между базами данных и возвращается код ошибки 40508. Для смены базы данных следует непосредственно подключиться к базе данных. Инструкция USE помечен как не применимо к базе данных SQL в верхней части этой страницы, поскольку, даже если может быть `USE` инструкции в пакете, он не выполняет никаких действий.
  
## <a name="remarks"></a>Замечания  
 При подключении имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа автоматически подключается к базе данных по умолчанию и получает контекст безопасности пользователя базы данных. Если для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь базы данных не был создан, имя входа подключается как «гость». Если пользователь базы данных не имеет разрешения CONNECT на базу данных, инструкция USE завершится ошибкой. Если с именем входа не была связана никакая база данных по умолчанию, то для него базой данных по умолчанию будет установлена база данных master.  
  
 Инструкция USE выполняется как на стадии компиляции, так и на стадии выполнения и вступает в силу немедленно. Иными словами, инструкции, которые содержатся в пакете после инструкции USE, будут выполнены в контексте указанной базы данных.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONNECT на целевую базу данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется смена контекста на базу данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере выполняется смена контекста на базу данных `AccountingDB`.  
  
```  
USE AccountingDB;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)  
  
  



