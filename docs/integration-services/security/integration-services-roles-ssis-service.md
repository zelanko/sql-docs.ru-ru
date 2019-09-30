---
title: Роли служб Integration Services (службы SSIS) | Документы Майкрософт
ms.custom: security
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3290aa2297ca849ed175b7db109f6b200debc789
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295674"
---
# <a name="integration-services-roles-ssis-service"></a>Роли служб Integration Services (службы SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляет конкретные предопределенные роли уровня базы данных для обеспечения безопасного доступа к пакетам, которые хранятся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Доступные роли зависят от того, где хранятся пакеты: в базе данных каталога служб SSIS (SSISDB) или в базе данных msdb.  
  
## <a name="roles-in-the-ssis-catalog-database-ssisdb"></a>Роли в базе данных каталога служб SSIS (SSISDB)  
 База данных каталога служб SSIS (SSISDB) предоставляет следующие предопределенные роли уровня базы данных, позволяющие обеспечить безопасный доступ к пакетам и сведениям о пакетах:  
  
-   **ssis_admin**— предоставляет полный административный доступ к базе данных каталога служб SSIS.  
  
-   **ssis_logreader** — предоставляет разрешение на доступ ко всем представлениям, связанным с операционными журналами SSISDB.  
  
     Список представлений включает в себя: [catalog].[projects], [catalog].[packages], [catalog].[operations], [catalog].[extended_operation_info], [catalog].[operation_messages], [catalog].[event_messages], [catalog].[execution_data_statistics], [catalog].[execution_component_phases], [catalog].[execution_data_taps], [catalog].[event_message_context], [catalog].[executions], [catalog].[executables], [catalog].[executable_statistics], [catalog].[validations], [catalog].[execution_parameter_values] и [catalog].[execution_property_override_values].  
  
## <a name="roles-in-the-msdb-database"></a>Роли в базе данных msdb  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат три предопределенные роли уровня базы данных, предназначенные для управления доступом к пакетам, которые сохранены в базе данных **msdb**: **db_ssisadmin**, **db_ssisltduser**и **db_ssisoperator** . С помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]можно назначить роль пакету. Назначения ролей сохраняются в базу данных **msdb** .  
  
### <a name="read-and-write-actions"></a>Действия чтения и записи  
 В следующей таблице приводятся операции чтения и записи Windows и предопределенных ролей уровня базы данных в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Роль|Операция чтения|Операция записи|  
|----------|-----------------|------------------|  
|**msdb**<br /><br /> или диспетчер конфигурации служб<br /><br /> **sysadmin**|Перечислить свои пакеты.<br /><br /> Перечислить все пакеты.<br /><br /> Посмотреть свои пакеты.<br /><br /> Посмотреть все пакеты.<br /><br /> Выполнить свои пакеты.<br /><br /> Выполнить все пакеты.<br /><br /> Экспортировать свои пакеты.<br /><br /> Экспортировать все пакеты.<br /><br /> Выполнить все пакеты агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Импортировать пакеты.<br /><br /> Удалить свои пакеты.<br /><br /> Удалить все пакеты.<br /><br /> Изменить роли своих пакетов.<br /><br /> Изменить роли всех пакетов.<br /><br /> <br /><br /> **\*\* Предупреждение. \*\*** Члены роли db_ssisadmin и роли dc_admin могут повышать свои права доступа до sysadmin. Такое повышение права доступа может произойти, так как эти роли могут изменять пакеты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , а пакеты [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] могут выполняться [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи контекста безопасности sysadmin агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы предотвратить такое повышение прав при выполнении планов обслуживания, наборов сбора данных и других пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , настройте задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запускающие пакеты, на использование учетной записи-посредника с ограниченными правами или добавьте членов sysadmin в роли db_ssisadmin и dc_admin.|  
|**db_ssisadmin**|Перечислить свои пакеты.<br /><br /> Перечислить все пакеты.<br /><br /> Посмотреть свои пакеты.<br /><br /> Выполнить свои пакеты.<br /><br /> Экспортировать свои пакеты.|Импортировать пакеты.<br /><br /> Удалить свои пакеты.<br /><br /> Изменить роли своих пакетов.|  
|**db_ssisltduser**|Перечислить все пакеты.<br /><br /> Посмотреть все пакеты.<br /><br /> Выполнить все пакеты.<br /><br /> Экспортировать все пакеты.<br /><br /> Выполнить все пакеты агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|None|  
|**Администраторы Windows**|Просмотреть подробности выполнения всех запущенных пакетов.|Остановить все выполняемые пакеты.|  
  
### <a name="sysssispackages-table"></a>Таблица Sysssispackages  
 Таблица **sysssispackages** базы данных **msdb** содержит пакеты, сохраненные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [sysssispackages (Transact-SQL)](../../relational-databases/system-tables/sysssispackages-transact-sql.md).  
  
 Таблица **sysssispackages** включает в себя столбцы, которые содержат сведения о ролях, назначенных пакетам.  
  
-   В столбце **readerrole** указывается роль, у которой есть право чтения из пакета.  
  
-   В столбце **writerrole** указывается роль, у которой есть право записи в пакет.  
  
-   Столбец **ownersid** содержит уникальный идентификатор безопасности пользователя, создавшего пакет. Этот столбец определяет владельца пакета.  
  
### <a name="permissions"></a>Разрешения  
 По умолчанию разрешения предопределенных ролей уровня базы данных **db_ssisadmin** и **db_ssisoperator** и уникальный идентификатор безопасности пользователя, создавшего пакет, применяются к роли модуля чтения пакета, а разрешение роли **db_ssisadmin** и уникальный идентификатор безопасности пользователя, создавшего пакет, применяются к роли модуля записи пакета. Пользователь должен быть членом роли **db_ssisadmin**, **db_ssisltduser**или **db_ssisoperator** , чтобы получить доступ на чтение пакета. Пользователь должен быть членом роли **db_ssisadmin** , чтобы получить доступ для записи.  
  
### <a name="access-to-packages"></a>Доступ к пакетам  
 Фиксированные роли уровня базы данных работают в сочетании с пользовательскими ролями. Пользовательские роли — это роли, которые создаются в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и после используются для назначения разрешений пакетам. Чтобы получить доступ к пакету, пользователь должен быть членом пользовательской роли и соответствующей предопределенной роли служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] уровня базы данных. Например, если пользователи являются членами определяемой пользователем роли **AuditUsers** , которая назначена пакету, они также должны быть членами роли **db_ssisadmin**, **db_ssisltduser**или **db_ssisoperator** , чтобы иметь доступ для чтения пакета.  
  
 Если пакетам не назначить пользовательских ролей, то доступом к пакетам будут управлять только предопределенные роли базы данных.  
  
 Если используются пользовательские роли, то перед тем как назначать их пакетам, нужно добавить их в базу данных **msdb** . Новую роль базы данных можно создать в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Роли уровня базы данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предоставляют право доступа к системным таблицам служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] базы данных msdb.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (служба MSSQLSERVER) должна быть запущена перед тем, как подключиться к ядру СУБД и базе данных **msdb** .  
  
 Чтобы назначить роли пакетов, необходимо выполнить следующие задачи.  
  
-   **Откройте обозреватель объектов и подключитесь к службам Integration Services**  
  
     Перед тем как с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]назначить роли для пакетов, необходимо открыть обозреватель объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и подключиться к службам [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] должна быть запущена перед подключением к [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Назначение пакетам ролей модулей чтения и записи**  
  
     Можно назначить роль чтения и модуля записи для каждого пакета.  

## <a name="assign"></a> Назначение пакетам роли чтения и модуля записи
  Можно назначить роль чтения и модуля записи для каждого пакета.  
  
### <a name="assign-a-reader-and-writer-role-to-a-package"></a>Назначение пакетам роли чтения и модуля записи  
  
1.  В обозревателе объектов найдите соединение служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Разверните папку «Сохраненные пакеты», затем разверните вложенную папку, содержащую пакеты, для которых необходимо назначить роли.  
  
3.  Щелкните правой кнопкой мыши на пакете, которому необходимо назначить роли.  
  
4.  В диалоговом окне **Роли пакета** выберите роль модуля чтения из списка **Роль модуля чтения** и роль модуля записи из списка **Роль модуля записи** .  
  
5.  Нажмите кнопку **ОК**.

## <a name="create"></a> Создание пользовательской роли
    
### <a name="to-create-a-user-defined-role"></a>Создание пользовательской роли  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  Щелкните **обозреватель объектов** в меню **Вид** .  
  
3.  На панели инструментов обозревателя объектов нажмите кнопку **Соединить**и выберите **Компонент Database Engine**.  
  
4.  В диалоговом окне **Соединение с сервером** введите имя сервера и выберите режим проверки подлинности. Для указания локального сервера можно использовать точку (.), (local) или **localhost** .  
  
5.  Нажмите кнопку **Соединить**.  
  
6.  Последовательно разверните узлы «Базы данных», «Системные базы данных», «msdb», «Безопасность» и «Роли».  
  
7.  В узле "Роли" щелкните правой кнопкой мыши элемент "Роли базы данных" и выберите **Создать роль базы данных**.  
  
8.  На странице «Общие» введите имя и при необходимости укажите владельца, схемы владельца и членов роли.  
  
9. При необходимости нажмите кнопку **Разрешения** и настройте разрешения объекта.  
  
10. При необходимости нажмите кнопку **Расширенные свойства** и настройте расширенные свойства.  
  
11. Нажмите кнопку **ОК**.

## <a name="roles_dialog"></a> Справочник по пользовательскому интерфейсу диалогового окна "Роли пакета"
  Используйте диалоговое окно **Роли пакетов** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], чтобы указать роли на уровне базы данных, которые обладают правами на считывание пакета, и роли на уровне базы данных, которые имеют права на запись пакета. Роли на уровне баз данных определяют права только для пакетов, хранящихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** .  
  
 Роли, список которых приведен в диалоговом окне, являются существующими в данный момент ролями системной базы данных **msdb** . Если роли не выбраны, то применяются роли служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] по умолчанию. По умолчанию в роль чтения включаются **db_ssisadmin**, **db_ssisoperator**и пользователь, создавший пакет. Пользователь, который является членом одной из этих ролей или является создателем пакета, может перечислять, просматривать, выполнять экспорт и запускать пакеты. По умолчанию в роль записи включается роль **db_ssisadmin** и пользователь, который создал пакет. Пользователь, который является членом этой роли, может выполнять импорт, удалять и изменять пакеты.  
  
 В столбце **ownersid** таблицы **sysssispackages** указан уникальный идентификатор безопасности пользователя, создавшего пакет.  
  
### <a name="options"></a>Параметры  
 **Имя пакета**  
 Укажите имя пакета.  
  
 **Роль считывания**  
 Выберите роль из списка.  
  
 **Роль записи**  
 Выберите роль из списка.  
