---
title: DROP DATABASE SCOPED CREDENTIAL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP DATABASE SCOPED CREDENTIAL
- DROP_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- DROP DATABASE SCOPED CREDENTIAL statement
- credential [SQL Server], DROP DATABASE SCOPED CREDENTIAL statement
ms.assetid: 319d59f4-fa82-47ca-869b-3a9cd52900b0
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ae5fceaf5b5eca88dfc147f03a8beeec5cd93c22
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970953"
---
# <a name="drop-database-scoped-credential-transact-sql"></a>DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Удаляет с сервера учетные данные для базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP DATABASE SCOPED CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Имя учетных данных для базы данных, которые необходимо удалить с сервера.  
  
## <a name="remarks"></a>Примечания  
 Чтобы удалить секрет, связанный с учетными данными для базы данных, не удаляя сами учетные данные, используйте [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md).  
  
 Дополнительные сведения об учетных данных для базы данных см. в представлении каталога [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `ALTER` на учетные данные.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются учетные данные с именем `SalesAccess` для базы данных.  
  
```sql  
DROP DATABASE SCOPED CREDENTIAL AppCred;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
