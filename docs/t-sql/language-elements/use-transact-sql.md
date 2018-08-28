---
title: USE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/28/2016
ms.prod: sql
ms.prod_service: pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3d342d76aa0e844a5e09316bde6bda99dc52da17
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43079518"
---
# <a name="use-transact-sql"></a>USE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Изменяет контекст базы данных на указанную базу данных или моментальный снимок базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
USE { database_name }   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных или моментального снимка базы данных, на который переключается контекст пользователя. Имена баз данных и моментальных снимков базы данных должны соответствовать правилам построения [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 В [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] параметр базы данных может ссылаться только на текущую базу данных. Если указана база данных, отличная от текущей, инструкция `USE` не переключается между базами данных и возвращается код ошибки 40508. Для смены базы данных следует непосредственно подключиться к базе данных. В верхней части этой страницы инструкция USE помечена как неприменимая к базе данных SQL, поскольку даже если инструкция `USE`входит в состав пакета, она не выполняет никаких действий.
  
## <a name="remarks"></a>Remarks  
 При подключении имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа автоматически подключается к базе данных по умолчанию и получает контекст безопасности пользователя базы данных. Если для имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пользователь базы данных не был создан, имя входа подключается как «гость». Если пользователь базы данных не имеет разрешения CONNECT на базу данных, инструкция USE завершится ошибкой. Если с именем входа не была связана никакая база данных по умолчанию, то для него базой данных по умолчанию будет установлена база данных master.  
  
 Инструкция USE выполняется как на стадии компиляции, так и на стадии выполнения и вступает в силу немедленно. Иными словами, инструкции, которые содержатся в пакете после инструкции USE, будут выполнены в контексте указанной базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONNECT на целевую базу данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется смена контекста на базу данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE LOGIN (Transact-SQL)](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)  
  
  


