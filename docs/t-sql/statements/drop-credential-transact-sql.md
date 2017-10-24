---
title: "DROP CREDENTIAL (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/19/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 99526bd72839ff483d39f0e78634ea27039388ae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет с сервера запись учетных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *credential_name*  
 Имя учетных данных, которые необходимо удалить с сервера.  
  
## <a name="remarks"></a>Замечания  
 Чтобы удалить секрет, связанный с учетными данными, не удаляя сами данные, используйте [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md).  
  
 Сведения об учетных данных отображается в **sys.credentials** представления каталога.  
  
> [!WARNING]  
>  Прокси связаны с учетными данными. Удаление учетных данных, используемых прокси-сервером, переводит связанный прокси-сервер в нерабочее состояние. При удалении учетных данных, используемых прокси-сервер, удалите прокси-сервер (с помощью [sp_delete_proxy &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md) и повторно создайте связанный прокси-сервер с помощью [sp_add_proxy &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение ALTER ANY CREDENTIAL. При удалении системных учетных данных требуется разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляются учетные данные `Saddles`.  
  
```  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Учетные данные &#40; компонент Database Engine &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

