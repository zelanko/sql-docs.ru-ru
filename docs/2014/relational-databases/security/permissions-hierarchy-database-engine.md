---
title: Иерархия разрешений (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: cf534ce7e56079d2578af7224c55b2c2cfb9d5e1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188193"
---
# <a name="permissions-hierarchy-database-engine"></a>Иерархия разрешений (компонент Database Engine)
  Компонент [!INCLUDE[ssDE](../../../includes/ssde-md.md)] управляет иерархической коллекцией сущностей, защита которых производится при помощи разрешений. Эти сущности называются *защищаемыми объектами*. Важнейшими защищаемыми компонентами являются серверы и базы данных, однако отдельные разрешения можно задавать на гораздо более глубоком уровне. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регулирует действия участников на защищаемых объектах, проверяя, что им были предоставлены соответствующие разрешения.  
  
 На следующей иллюстрации показана связь между иерархиями разрешений компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .  
  
 ![Диаграмма иерархии разрешений для ядра СУБД](../../database-engine/media/wj-security-layers.gif "Диаграмма иерархии разрешений для ядра СУБД")  
  
## <a name="chart-of-sql-server-permissions"></a>Диаграмма разрешений SQL Server  
 Схему плакатного размера всех разрешений компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] в формате PDF см. по ссылке [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## <a name="working-with-permissions"></a>Работа с разрешениями  
 Выполнение различных действий с разрешениями осуществляется при помощи обычных запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] : GRANT, DENY и REVOKE. Сведения о разрешениях доступны через представления каталога [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) и [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) . Существует также поддержка запроса сведений о разрешениях при помощи встроенных функций.  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности SQL Server](securing-sql-server.md)   
 [Разрешения (компонент Database Engine)](permissions-database-engine.md)   
 [Securables](securables.md)   
 [Участники (ядро СУБД)](authentication-access/principals-database-engine.md)   
 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql)   
 [DENY (Transact-SQL)](/sql/t-sql/statements/deny-transact-sql)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](/sql/t-sql/functions/has-perms-by-name-transact-sql)   
 [sys.fn_builtin_permissions (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [sys.server_permissions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)   
 [sys.database_permissions (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
