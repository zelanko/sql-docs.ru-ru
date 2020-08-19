---
description: DROP REMOTE SERVICE BINDING (Transact-SQL)
title: DROP REMOTE SERVICE BINDING (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP REMOTE SERVICE BINDING
- DROP_REMOTE_SERVICE_BINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping remote service bindings
- removing remote service bindings
- deleting remote service bindings
- remote service bindings [Service Broker], dropping
- DROP REMOTE SERVICE BINDING statement
ms.assetid: 377789b4-bf94-488f-8c20-687d0bae447a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f35d18ea74041bf21b1f67010333ff73b3ef808c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444655"
---
# <a name="drop-remote-service-binding-transact-sql"></a>DROP REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет привязку удаленной службы.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
DROP REMOTE SERVICE BINDING binding_name  
[ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *binding_name*  
 Имя привязки удаленной службы, которую планируется удалить. Не могут быть указаны имена сервера, базы данных и схемы.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешение на удаление привязки удаленной службы принадлежит владельцу привязки удаленной службы, членам предопределенной роли db_owner базы данных и членам предопределенной роли сервера sysadmin.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется удаление привязки удаленной службы `APBinding` из базы данных.  
  
```  
DROP REMOTE SERVICE BINDING APBinding ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE REMOTE SERVICE BINDING (Transact-SQL)](../../t-sql/statements/create-remote-service-binding-transact-sql.md)   
 [ALTER REMOTE SERVICE BINDING (Transact-SQL)](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
