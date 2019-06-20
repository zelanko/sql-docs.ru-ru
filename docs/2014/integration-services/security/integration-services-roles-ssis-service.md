---
title: Роли служб Integration Services (службы SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 43c1c932565ae3df666be10a1b89794ecd720135
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62766676"
---
# <a name="integration-services-roles-ssis-service"></a>Роли служб Integration Services (службы SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат три предопределенные роли уровня базы данных, `db_ssisadmin`, **db_ssisltduser**, и **db_ssisoperator**, для управления доступом к пакетам. Роли могут быть реализованы только для пакетов, сохраненных в `msdb` базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]можно назначить роль пакету. Назначения ролей сохраняются в `msdb` базы данных.  
  
## <a name="read-and-write-actions"></a>Действия чтения и записи  
 В следующей таблице приводятся операции чтения и записи Windows и предопределенных ролей уровня базы данных в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Роль|Операция чтения|Операция записи|  
|----------|-----------------|------------------|  
|`db_ssisadmin`<br /><br /> или диспетчер конфигурации служб<br /><br /> `sysadmin`|Перечислить свои пакеты.<br /><br /> Перечислить все пакеты.<br /><br /> Посмотреть свои пакеты.<br /><br /> Посмотреть все пакеты.<br /><br /> Выполнить свои пакеты.<br /><br /> Выполнить все пакеты.<br /><br /> Экспортировать свои пакеты.<br /><br /> Экспортировать все пакеты.<br /><br /> Выполнить все пакеты агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Импортировать пакеты.<br /><br /> Удалить свои пакеты.<br /><br /> Удалить все пакеты.<br /><br /> Изменить роли своих пакетов.<br /><br /> Изменить роли всех пакетов.<br /><br /> <br /><br /> **\*\* Важные \* \***  члены роли db_ssisadmin и роли dc_admin могут повышать свои права доступа до sysadmin. Такое повышение права доступа может произойти, так как эти роли могут изменять пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , а пакеты [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут выполняться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи контекста безопасности sysadmin агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы предотвратить такое повышение прав при выполнении планов обслуживания, наборов сбора данных и других пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , настройте задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запускающие пакеты, на использование учетной записи-посредника с ограниченными правами или добавьте членов sysadmin в роли db_ssisadmin и dc_admin.|  
|**db_ssisadmin**|Перечислить свои пакеты.<br /><br /> Перечислить все пакеты.<br /><br /> Посмотреть свои пакеты.<br /><br /> Выполнить свои пакеты.<br /><br /> Экспортировать свои пакеты.|Импортировать пакеты.<br /><br /> Удалить свои пакеты.<br /><br /> Изменить роли своих пакетов.|  
|**db_ssisltduser**|Перечислить все пакеты.<br /><br /> Посмотреть все пакеты.<br /><br /> Выполнить все пакеты.<br /><br /> Экспортировать все пакеты.<br /><br /> Выполнить все пакеты агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|None|  
|**Администраторы Windows**|Просмотреть подробности выполнения всех запущенных пакетов.|Остановить все выполняемые пакеты.|  
  
## <a name="sysssispackages-table"></a>Таблица Sysssispackages  
 **Sysssispackages** в таблицу `msdb` содержит пакеты, сохраненные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [sysssispackages (Transact-SQL)](/sql/relational-databases/system-tables/sysssispackages-transact-sql).  
  
 Таблица **sysssispackages** включает в себя столбцы, которые содержат сведения о ролях, назначенных пакетам.  
  
-   В столбце **readerrole** указывается роль, у которой есть право чтения из пакета.  
  
-   В столбце **writerrole** указывается роль, у которой есть право записи в пакет.  
  
-   Столбец **ownersid** содержит уникальный идентификатор безопасности пользователя, создавшего пакет. Этот столбец определяет владельца пакета.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию, разрешения `db_ssisadmin` и **db_ssisoperator** предопределенные роли уровня базы данных и уникальный идентификатор безопасности пользователя, создавшего пакет, применяются к роли модуля чтения пакетов, а также разрешения `db_ssisadmin` роли и уникальный идентификатор безопасности пользователя, создавшего пакет, применяются к роли модуля записи. Пользователь должен быть членом `db_ssisadmin`, **db_ssisltduser**, или **db_ssisoperator** роль должна иметь доступ на чтение к пакету. Пользователь должен быть членом `db_ssisadmin` роль должна иметь доступ на запись.  
  
## <a name="access-to-packages"></a>Доступ к пакетам  
 Фиксированные роли уровня базы данных работают в сочетании с пользовательскими ролями. Пользовательские роли — это роли, которые создаются в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и после используются для назначения разрешений пакетам. Чтобы получить доступ к пакету, пользователь должен быть членом пользовательской роли и соответствующей предопределенной роли служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] уровня базы данных. Например, если пользователи являются членами **AuditUsers** определяемой пользователем роли, назначенной для пакета, они также должны быть членами `db_ssisadmin`, **db_ssisltduser**, или **db_ ssisoperator** роль должна иметь доступ на чтение к пакету.  
  
 Если пакетам не назначить пользовательских ролей, то доступом к пакетам будут управлять только предопределенные роли базы данных.  
  
 Если вы хотите использовать определяемые пользователем роли, необходимо добавить их к `msdb` базы данных перед тем как назначать их пакетам. Новую роль базы данных можно создать в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Роли уровня базы данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют право доступа к системным таблицам служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] базы данных msdb.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (служба MSSQLSERVER) должна запускаться перед подключением к ядру СУБД и `msdb` базы данных.  
  
 Чтобы назначить роли пакетов, необходимо выполнить следующие задачи.  
  
-   **Откройте обозреватель объектов и подключитесь к службам Integration Services**  
  
     Перед тем как с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]назначить роли для пакетов, необходимо открыть обозреватель объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и подключиться к службам [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] должна быть запущена перед подключением к [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Назначение пакетам ролей модулей чтения и записи**  
  
     Можно назначить роль чтения и модуля записи для каждого пакета.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Назначение пакетам роли чтения и модуля записи](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Создание пользовательской роли](../create-a-user-defined-role.md)  
  
-   [Подключение к службам Integration Services](../connect-to-integration-services.md)  
  
  
