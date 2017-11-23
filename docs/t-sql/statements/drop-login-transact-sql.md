---
title: "DROP LOGIN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP LOGIN
- DROP_LOGIN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- deleting login accounts
- logins [SQL Server], removing
- DROP LOGIN statement
- removing login accounts
- dropping login accounts
ms.assetid: acb5c3dc-7aa2-49f6-9330-573227ba9b1a
caps.latest.revision: "36"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e43f37e0aa24cf6ab1ac7b01b378e461e5dea706
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="drop-login-transact-sql"></a>DROP LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Удаляет учетную запись входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP LOGIN login_name  
```  
  
## <a name="arguments"></a>Аргументы  
 *login_name*  
 Задает имя входа для удаления.  
  
## <a name="remarks"></a>Замечания  
 Нельзя удалить текущее имя входа. Также нельзя удалить имя входа, владеющее любым защищаемым объектом уровня сервера или заданием агента SQL Server.  
  
 Можно удалить имена входа, сопоставленные пользователям базы данных; однако это приведет к появлению пользователей, утративших связь с учетными записями. Дополнительные сведения см. в статье [Диагностика пользователей, утративших связь с учетной записью (SQL Server)](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md).  
  
 В [!INCLUDE[ssSDS](../../includes/sssds-md.md)], требуются данные входа для проверки подлинности подключения и правила брандмауэра уровня сервера временно кэшируются в каждой базе данных. Этот кэш периодически обновляется. Чтобы принудительно обновить кэш проверки подлинности и убедитесь в том, что база данных имеет последнюю версию таблицы, имена входа, выполните [DBCC FLUSHAUTHCACHE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER ANY LOGIN на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-dropping-a-login"></a>A. Удаление имени входа  
 В данном примере удаляется имя входа `WilliJo`.  
  
```  
DROP LOGIN WilliJo;  
GO 
```  
 
  
## <a name="see-also"></a>См. также:  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  

