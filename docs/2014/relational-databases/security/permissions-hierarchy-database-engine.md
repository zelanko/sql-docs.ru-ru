---
title: Иерархия разрешений (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
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
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 607ac55fe426cd086ce31ade33d3e772e7a3d9a9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487157"
---
# <a name="permissions-hierarchy-database-engine"></a>Иерархия разрешений (компонент Database Engine)
  Компонент [!INCLUDE[ssDE](../../../includes/ssde-md.md)] управляет иерархической коллекцией сущностей, защита которых производится при помощи разрешений. Эти сущности называются *защищаемыми объектами*. Важнейшими защищаемыми компонентами являются серверы и базы данных, однако отдельные разрешения можно задавать на гораздо более глубоком уровне. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регулирует действия участников на защищаемых объектах, проверяя, что им были предоставлены соответствующие разрешения.

 На следующей иллюстрации показана связь между иерархиями разрешений компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .

 ![Диаграмма иерархий разрешений в ядре СУБД](../../database-engine/media/wj-security-layers.gif "Диаграмма иерархий разрешений в ядре СУБД")

## <a name="chart-of-sql-server-permissions"></a>Диаграмма разрешений SQL Server
 Для диаграммы размером [!INCLUDE[ssDE](../../../includes/ssde-md.md)] с плакат всех [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf)разрешений в формате pdf см.

## <a name="working-with-permissions"></a>Работа с разрешениями
 Выполнение различных действий с разрешениями осуществляется при помощи обычных запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] : GRANT, DENY и REVOKE. Сведения о разрешениях доступны через представления каталога [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) и [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) . Существует также поддержка запроса сведений о разрешениях при помощи встроенных функций.

## <a name="see-also"></a>См. также:
 [Обеспечение безопасности sL Server](securing-sql-server.md) [Permissions &#40;Database Engine&#41;](permissions-database-engine.md) [Securables](securables.md) [Принципы &#40;database Engine&#41;](authentication-access/principals-database-engine.md) GRANT &#40;[Transact-S'S-l&#41;](/sql/t-sql/statements/grant-transact-sql) REVOKE &#40;[Database_permissions-Си-СЗЛ&#41;](/sql/t-sql/statements/revoke-transact-sql) DENY &#40;Database_permissions&#41;[&#40;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)&#41;&#40;[server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)&#41;&#40;[fn_builtin_permissions](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)&#41;&#40;[HAS_PERMS_BY_NAME](/sql/t-sql/functions/has-perms-by-name-transact-sql)&#41;[Database_permissions](/sql/t-sql/statements/deny-transact-sql)


