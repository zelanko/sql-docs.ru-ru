---
title: "sys.sp_rda_reauthorize_db (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_rda_reauthorize_db
- sp_rda_reauthorize_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_reauthorize_db stored procedure
ms.assetid: f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55c8e5167997ceb944cdce51b9d73b651c347396
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="syssprdareauthorizedb-transact-sql"></a>sys.sp_rda_reauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Восстанавливает подключение с проверкой подлинности между локальной базы данных включена для Stretch и удаленной базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_rda_reauthorize_db @credential = @credential, @with_copy = @with_copy [ , @azure_servername = @azure_servername, @azure_databasename = @azure_databasename ]  
```  
  
## <a name="arguments"></a>Аргументы  
 @credential = *@credential*  
 Представляет учетные данные уровня базы данных, связанные с локальной базы данных с включенным Stretch.  
  
 @with_copy = *@with_copy*  
 Указывает, следует ли сделать копию удаленных данных и подключиться к копии (рекомендуется). *@with_copy*имеет тип bit.  
  
 @azure_servername = *@azure_servername*  
 Указывает имя сервера Azure, который содержит удаленные данные. *@azure_servername*имеет тип sysname.  
  
 @azure_databasename = *@azure_databasename*  
 Указывает имя базы данных Azure, которая содержит удаленные данные. *@azure_databasename*имеет тип sysname.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или >0 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуются права db_owner.  
  
## <a name="remarks"></a>Remarks  
 При запуске [sys.sp_rda_reauthorize_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) для повторного подключения к удаленной базе данных Azure, эта операция автоматически восстанавливает режим запроса LOCAL_AND_REMOTE, что является поведением по умолчанию для базы данных Stretch. То есть запросы возвращают результаты из локальных и удаленных данных.  
  
## <a name="example"></a>Пример  
 В следующем примере восстанавливается подключение с проверкой подлинности между локальной базы данных включена для Stretch и удаленной базе данных. Он создает копию удаленных данных (рекомендуется) и подключается к новой копии.  
  
```sql  
DECLARE @credentialName nvarchar(128);   
SET @credentialName = N'<existing_database_scoped_credential_name>';   
EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.sp_rda_deauthorize_db &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
