---
description: DROP CREDENTIAL (Transact-SQL)
title: DROP CREDENTIAL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CREDENTIAL
- DROP_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing credentials
- DROP CREDENTIAL statement
- credentials [SQL Server], DROP CREDENTIAL statement
- authentication [SQL Server], credentials
- deleting credentials
- dropping credentials
ms.assetid: df22c826-317d-45a6-b078-186acb65f71e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9f50d075b23df010e1a79a6b83283e8a6bcdb9b0
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380112"
---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет учетные данные с сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DROP CREDENTIAL credential_name  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *credential_name*  
 Имя учетных данных, которые необходимо удалить с сервера.  
  
## <a name="remarks"></a>Комментарии  
 Чтобы удалить секрет, связанный с учетными данными, не удаляя сами данные, используйте [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md).  
  
 Сведения об учетных данных отображаются в представлении каталога **sys.credentials**.  
  
> [!WARNING]  
>  Прокси связаны с учетными данными. Удаление учетных данных, используемых прокси-сервером, переводит связанный прокси-сервер в нерабочее состояние. При удалении учетных данных, используемых прокси-сервером, удалите прокси-сервер с помощью [sp_delete_proxy (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md) и повторно создайте связанный прокси-сервер с помощью [sp_add_proxy (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY CREDENTIAL. При удалении системных учетных данных требуется разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются учетные данные `Saddles`.  
  
```sql  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
