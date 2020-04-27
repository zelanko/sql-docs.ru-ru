---
title: Каталог служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 14de3fa15fa5a648c2d41824d237040b5aa085e5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62771580"
---
# <a name="ssis-catalog"></a>Каталог служб SSIS
  `SSISDB` Каталог является центральной точкой для работы с [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] проектами служб (SSIS), развернутыми на [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сервере. Например, можно задавать параметры проектов и пакетов, настраивать среды для указания значений времени выполнения для пакетов, выполнять пакеты и проводить устранение неполадок, а также управлять операциями на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Объекты, хранящиеся в `SSISDB` каталоге, включают в себя проекты, пакеты, параметры, среды и журнал операций.  
  
 Проверяются объекты, параметры и операционные данные, хранящиеся в `SSISDB` каталоге, путем запроса представлений в `SSISDB` базе данных. Управление объектами осуществляется путем вызова хранимых процедур в `SSISDB` базе данных или с помощью пользовательского интерфейса `SSISDB` каталога. Во многих случаях одну и ту же задачу можно выполнить и в пользовательском интерфейсе, и путем вызова хранимой процедуры.  
  
 Чтобы обеспечить поддержку базы данных `SSISDB`, рекомендуется применять предопределенные политики предприятия для управления пользовательскими базами данных. Дополнительные сведения о создании планов обслуживания см. в разделе [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md).  
  
 `SSISDB` Каталог и `SSISDB` база данных поддерживают Windows PowerShell. Дополнительные сведения об использовании SQL Server с Windows PowerShell см. в разделе [SQL Server PowerShell](../../powershell/sql-server-powershell.md). Примеры использования Windows PowerShell для выполнения задач, например таких как развертывание проекта, см. в записи блога [SSIS и Powershell в SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539)на сайте blogs.msdn.com.  
  
 Дополнительные сведения о просмотре данных операций см. в разделе [мониторинг выполнения пакетов и других операций](../performance/monitor-running-packages-and-other-operations.md).  
  
 Чтобы получить доступ `SSISDB` к каталогу [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , подключитесь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к ядро СУБД, а затем разверните узел **каталоги Integration Services** в обозревателе объектов. Доступ к `SSISDB` базе данных можно [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] получить, развернув узел базы данных в обозревателе объектов.  
  
> [!NOTE]  
>  Переименовать `SSISDB` базу данных нельзя.  
  
> [!NOTE]  
>  Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр, к которому `SSISDB` присоединена база данных, останавливается или не отвечает, процесс ISServerExec. exe завершается. Сообщение записывается в журнал событий Windows.  
>   
>  Если ресурсы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переходят на другой ресурс в процессе отработки отказа кластера, выполняемые пакеты не перезапускаются. Перезапуск пакетов вы можете выполнять с помощью контрольных точек. Дополнительные сведения см. в разделе [Restart Packages by Using Checkpoints](../packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="catalog-object-identifiers"></a>Идентификаторы объектов каталога  
 При создании нового объекта в каталоге необходимо назначить имя объекта. Идентификатором объекта является его имя. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет правила, указывающие, какие символы могут использоваться в идентификаторе. Имена следующих объектов должны соответствовать правилам для идентификаторов.  
  
-   Папка  
  
-   Проект  
  
-   Среда  
  
-   Параметр  
  
-   Переменная среды  
  
### <a name="folder-project-environment"></a>Папка, проект, среда  
 Учитывайте следующие правила при переименовании папки, проекта или среды.  
  
-   Недопустимы символы ASCII и Юникода с кодами от 1 до 31, символ двойных кавычек ("), символ "меньше" (\<), символ "больше" (>), символ вертикальной черты (|), знак возврата на один символ (\b), символ NULL (\0) и знак табуляции (\t).  
  
-   Имя не должно содержать начальных и конечных пробелов.  
  
-   \@ нельзя использовать в качестве первого символа. \@ может использоваться в качестве последующих символов.  
  
-   Длина имени должна быть больше 0 и меньше или равна 128.  
  
### <a name="parameter"></a>Параметр  
 Принимайте во внимание следующие правила при именовании параметра.  
  
-   Первым символом имени должна быть буква, по определению стандарта Юникод 2.0, или символ подчеркивания (_).  
  
-   Далее могут следовать буквы или цифры, по определению стандарта Юникод 2.0, или символы подчеркивания (_).  
  
### <a name="environment-variable"></a>Переменная среды  
 Учитывайте следующие правила при наименовании переменной среды  
  
-   Недопустимы символы ASCII и Юникода с кодами от 1 до 31, символ двойных кавычек ("), символ "меньше" (\<), символ "больше" (>), символ вертикальной черты (|), знак возврата на один символ (\b), символ NULL (\0) и знак табуляции (\t).  
  
-   Имя не должно содержать начальных и конечных пробелов.  
  
-   \@ нельзя использовать в качестве первого символа. \@ может использоваться в качестве последующих символов.  
  
-   Длина имени должна быть больше 0 и меньше или равна 128.  
  
-   Первым символом имени должна быть буква, по определению стандарта Юникод 2.0, или символ подчеркивания (_).  
  
-   Далее могут следовать буквы или цифры, по определению стандарта Юникод 2.0, или символы подчеркивания (_).  
  
## <a name="catalog-configuration"></a>Конфигурация каталога  
 Для точной настройки поведения каталога измените свойства каталога. Свойства каталога определяют методы шифрования конфиденциальных данных и способы хранения данных об управлении версиями операций и проектов. Задать свойства каталога можно в диалоговом окне **Свойства каталога** или с помощью хранимой процедуры [catalog.configure_catalog (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database). Просмотреть свойства можно в диалоговом окне или с помощью запроса [catalog.catalog_properties (база данных SSISDB)](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database). Диалоговое окно можно открыть, щелкнув `SSISDB` правой кнопкой мыши в обозревателе объектов.  
  
### <a name="operations-and-project-version-cleanup"></a>Очистка версий операций и проектов  
 Данные о состоянии для многих из этих операций в каталоге хранятся во внутренних таблицах базы данных. Например, каталог отслеживает состояние выполнения пакета и развертывания проекта. Чтобы поддерживался размер данных операций, для удаления старых данных используется **задание по обслуживанию служб SSIS** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Это задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается при установке служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Вы можете обновить или повторно развернуть проект [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с тем же именем в той же папке в каталоге. По умолчанию каждый раз при повторном развертывании проекта `SSISDB` каталог содержит предыдущую версию проекта. Чтобы поддерживался размер данных операций, для удаления старых версий проектов используется **задание обслуживания сервера служб SSIS** .  
  
 Следующие `SSISDB` свойства каталога определяют работу этого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента. Просмотреть и изменить свойства вы можете в диалоговом окне **Свойства каталога** или с помощью процедур [catalog.catalog_properties (база данных SSISDB)](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) и [catalog.configure_catalog (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 **Периодическая очистка журналов**  
 Шаг задания для очистки операций запускается в том случае, если это свойство имеет значение `True`.  
  
 **Срок хранения (в днях)**  
 Определяет максимальный срок хранения данных о допустимых операциях (в днях). Более старые данные удаляются.  
  
 Минимальное значение срока хранения — 1 день. Максимальное значение ограничено только максимальным значением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `int` данных. Сведения об этом типе данных см. в разделе [int, bigint, smallint, and tinyint (Transact-SQL)](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql).  
  
 **Периодическое удаление старых версий**  
 Шаг задания для очистки версий проекта запускается в том случае, если это свойство имеет значение `True`.  
  
 **Максимальное количество версий в проекте**  
 Определяет, сколько версий проекта будет храниться в каталоге. Более старые версии проектов удаляются.  
  
### <a name="encryption-algorithm"></a>Алгоритм шифрования  
 Свойство **Алгоритм шифрования** указывает тип шифрования, который используется при шифровании значений конфиденциальных параметров. Вы можете выбрать из следующих типов шифрования.  
  
-   AES_256 (по умолчанию)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 При развертывании проекта [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]каталог автоматически шифрует данные пакета и конфиденциальные значения. Каталог также автоматически расшифровывает данные после их получения. Каталог SSISDB использует уровень защиты `ServerStorage`. Дополнительные сведения см. в разделе [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
 Изменение алгоритма шифрования занимает длительное время. Сначала сервер использует указанный ранее алгоритм для расшифровки всех значений конфигурации. Затем сервер использует новый алгоритм для повторного шифрования значений. При выполнении этого процесса на сервере не могут выполняться другие операции служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Таким образом, чтобы обеспечить непрерывное выполнение операций служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , для алгоритма шифрования задается значение только для чтения в диалоговом окне в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Чтобы изменить значение свойства **алгоритма шифрования** , задайте для `SSISDB` базы данных однопользовательский режим, а затем вызовите хранимую процедуру catalog. configure_catalog. Используйте ENCRYPTION_ALGORITHM для аргумента *property_name*. Список поддерживаемых значений свойств см. в разделе [catalog.catalog_properties (база данных SSISDB)](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database). Дополнительные сведения о хранимой процедуре см. в разделе [catalog.configure_catalog (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 Дополнительные сведения об однопользовательском режиме см. в разделе [Установка однопользовательского режима базы данных](../../relational-databases/databases/set-a-database-to-single-user-mode.md). Дополнительные сведения о шифровании и алгоритмах шифрования в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в подразделах раздела [Шифрование SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md).  
  
 Для шифрования используется главный ключ базы данных. Ключ создается при создании каталога. Дополнительные сведения см. в разделе [Создание каталога служб SSIS](ssis-catalog.md).  
  
 В следующей таблице приведены имена свойств, показанных в диалоговом окне **Свойства каталога** , а также соответствующие свойства в представлении базы данных.  
  
|Имя свойства (диалоговое окно "**свойства каталога** ")|Имя свойства (представление базы данных)|  
|---------------------------------------------------------|-------------------------------------|  
|Имя алгоритма шифрования|ENCRYPTION_ALGORITHM|  
|Периодическая очистка журналов|OPERATION_CLEANUP_ENABLED|  
|Срок хранения (в днях)|RETENTION_WINDOW|  
|Периодическое удаление старых версий|VERSION_CLEANUP_ENABLED|  
|Максимальное количество версий в проекте|MAX_PROJECT_VERSIONS|  
|Серверное значение уровня ведения журнала по умолчанию|SERVER_LOGGING_LEVEL|  
  
## <a name="permissions"></a>Разрешения  
 Проекты, среды и пакеты содержатся в папках, которые являются защищаемыми объектами. Вы можете предоставить разрешения для папки, включая разрешение MANAGE_OBJECT_PERMISSIONS. Разрешение MANAGE_OBJECT_PERMISSIONS позволяет делегировать пользователю разрешения на администрирование содержимого папки, не предоставляя ему членства в роли ssis_admin. Вы можете также предоставлять разрешения проектам, средам и операциям. К операциям [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]относятся инициализация, развертывание проектов, создание и запуск выполнения, проверка проектов и пакетов, а `SSISDB` также Настройка каталога.  
  
 Дополнительные сведения о ролях баз данных см. в разделе [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 В каталоге SSISDB используется триггер DDL ddl_cleanup_object_permissions для принудительного обеспечения целостности сведений о разрешениях для защищаемых объектов служб SSIS. Триггер срабатывает, когда участник базы данных, например пользователь базы данных, роль базы данных или роль приложения базы данных, удаляется из базы данных SSISDB.  
  
 Если участник предоставлял или запрещал права доступа другим участникам, их необходимо отменить, прежде чем можно будет удалить этого участника. В противном случае возвращается сообщение об ошибке, если система пытается удалить участника. Триггер удаляет все записи разрешений, в которых участник базы данных является получателем разрешений.  
  
 Рекомендуется, чтобы триггер не был отключен, так как он гарантирует отсутствие потерянных записей разрешений после удаления участника базы данных из `SSISDB` базы данных.  
  
### <a name="managing-permissions"></a>Управление разрешениями  
 Вы можете управлять разрешениями на основе пользовательского интерфейса [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , хранимых процедур и пространства имен <xref:Microsoft.SqlServer.Management.IntegrationServices> .  
  
 Для управления разрешениями с помощью пользовательского интерфейса [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используются следующие диалоговые окна.  
  
-   Для папки пользуйтесь страницей **Разрешения** в диалоговом окне [Folder Properties Dialog Box](folder-properties-dialog-box.md)  
  
-   Для проекта пользуйтесь страницей **Разрешения** в диалоговом окне [Project Properties Dialog Box](project-properties-dialog-box.md).  
  
 Для управления разрешениями с помощью Transact-SQL вызовите процедуру [catalog.grant_permission (SSISDB Database)](/sql/integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database), [catalog.deny_permission (SSISDB Database)](/sql/integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database) или [catalog.revoke_permission (SSISDB Database)](/sql/integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database). Чтобы просмотреть действующие разрешения текущего участника для всех объектов, выполните запрос [catalog.effective_object_permissions (база данных SSISDB)](/sql/integration-services/system-views/catalog-effective-object-permissions-ssisdb-database). В этом разделе содержатся описания различных типов разрешений. Для просмотра разрешений, явным образом назначенных пользователю, выполните запрос [catalog.explicit_object_permissions (база данных SSISDB)](/sql/integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database).  
  
## <a name="folders"></a>Папки  
 Папка содержит один или несколько проектов и сред в `SSISDB` каталоге. Вы можете использовать представление [catalog.folders (база данных SSISDB)](/sql/integration-services/system-views/catalog-folders-ssisdb-database) для получения доступа к сведениям о папках в каталоге. Для управления папками вы можете использовать следующие хранимые процедуры.  
  
-   [catalog.create_folder (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database)  
  
-   [catalog.delete_folder (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database)  
  
-   [catalog.rename_folder (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database)  
  
-   [catalog.set_folder_description (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database)  
  
## <a name="projects-and-packages"></a>Проекты и пакеты  
 Каждый проект может содержать несколько пакетов. Как проекты, так и пакеты могут содержать параметры и ссылки на среды. Доступ к параметрам и ссылкам на среды возможен с использованием [Configure Dialog Box](configure-dialog-box.md).  
  
 Вы можете выполнять другие задачи администрирования проекта, вызывая следующие хранимые процедуры.  
  
-   [catalog.delete_project (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database)  
  
-   [catalog.deploy_project (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database)  
  
-   [catalog.get_project (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database)  
  
-   [catalog.move_project (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-move-project-ssisdb-database)  
  
-   [catalog.restore_project (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database)  
  
 Эти представления содержат сведения о пакетах, проектах и версиях проектов.  
  
-   [catalog.projects (база данных SSISDB)](/sql/integration-services/system-views/catalog-projects-ssisdb-database)  
  
-   [catalog.packages (база данных SSISDB)](/sql/integration-services/system-views/catalog-packages-ssisdb-database)  
  
-   [catalog.object_versions (база данных SSISDB)](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database)  
  
## <a name="parameters"></a>Параметры  
 Параметры используются для присвоения значений свойствам пакета во время выполнения пакета. Для задания значения параметра проекта или пакета и очистки этого значения следует вызвать процедуру [catalog.set_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) или [catalog.clear_object_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database). Чтобы задать значение параметра для экземпляра выполнения, следует вызвать [catalog.set_execution_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database). Значения параметров по умолчанию можно получить, вызвав процедуру [catalog.get_parameter_values (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database).  
  
 Эти представления показывают параметры для всех пакетов и проектов, а также значения параметров, используемые для экземпляра выполнения.  
  
-   [catalog.object_parameters (база данных SSISDB)](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database)  
  
-   [catalog.execution_parameter_values (база данных SSISDB)](/sql/integration-services/system-views/catalog-execution-parameter-values-ssisdb-database)  
  
## <a name="server-environments-server-variables-and-server-environment-references"></a>Серверные среды, переменные сервера и ссылки на серверные среды  
 Серверные среды содержат переменные сервера. Значения переменных могут использоваться при выполнении или проверке пакета на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Следующие хранимые процедуры позволяют выполнять многие другие задачи управления для сред и переменных.  
  
-   [catalog.create_environment (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database)  
  
-   [catalog.delete_environment (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database)  
  
-   [catalog.move_environment (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database)  
  
-   [catalog.rename_environment (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database)  
  
-   [catalog.set_environment_property (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database)  
  
-   [catalog.create_environment_variable (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database)  
  
-   [catalog.delete_environment_variable (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database)  
  
-   [catalog.set_environment_variable_property (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database)  
  
-   [catalog.set_environment_variable_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database)  
  
 Вызов хранимой процедуры [catalog.set_environment_variable_protection (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database) позволит установить бит конфиденциальности для переменной.  
  
 Для использования значения серверной переменной необходимо указать ссылку между проектом и серверной средой. Вы можете использовать следующие хранимые процедуры создания и удаления ссылок. Вы можете также указать, может ли среда находиться в той же папке, что и проект, или в другой папке.  
  
-   [catalog.create_environment_reference (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database)  
  
-   [catalog.delete_environment_reference (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database)  
  
-   [catalog.set_environment_reference_type (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database)  
  
 Чтобы получить дополнительные сведения о средах и переменных, выполните запрос к этим представлениям.  
  
-   [catalog.environments (база данных SSISDB)](/sql/integration-services/system-views/catalog-environments-ssisdb-database)  
  
-   [catalog.environment_variables (база данных SSISDB)](/sql/integration-services/system-views/catalog-environment-variables-ssisdb-database)  
  
-   [catalog.environment_references (база данных SSISDB)](/sql/integration-services/system-views/catalog-environment-references-ssisdb-database)  
  
## <a name="executions-and-validations"></a>Выполнения и проверки  
 Выполнение — это экземпляр выполнения пакета. Процедуры [catalog.create_execution (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) и [catalog.start_execution (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) позволяют настроить и запустить выполнение пакета. Чтобы остановить выполнение или проверку пакета или проекта, вызовите [catalog.stop_operation (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).  
  
 Для приостановки выполняемого пакета и создания файла дампа вызовите хранимую процедуру catalog.create_execution_dump. Файл дампа предоставляет сведения о выполнении пакета, которые могут быть полезны при диагностике неполадок в ходе выполнения. Дополнительные сведения о создании и настройке файлов дампа см. в разделе [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).  
  
 Выполняйте запросы к этим представлениям для получения сведений о выполнениях, проверках и сообщениях, регистрируемых в ходе операций, а также контекстных сведений, связанных с ошибками.  
  
-   [catalog.executions (база данных SSISDB)](/sql/integration-services/system-views/catalog-executions-ssisdb-database)  
  
-   [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database)  
  
-   [catalog.operation_messages (база данных SSISDB)](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database)  
  
-   [catalog.extended_operation_info (база данных SSISDB)](/sql/integration-services/system-views/catalog-extended-operation-info-ssisdb-database)  
  
-   [catalog.event_messages](/sql/integration-services/system-views/catalog-event-messages)  
  
-   [catalog.event_message_context](/sql/integration-services/system-views/catalog-event-message-context)  
  
 Для проверки проектов и пакетов можно вызвать хранимые процедуры [catalog.validate_project (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database) и [catalog.validate_package (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database). Представление [catalog.validations (база данных SSISDB)](/sql/integration-services/system-views/catalog-validations-ssisdb-database) содержит сведения о таких проверках, как ссылки серверной среды, учитываемые при проверке, имеет ли место проверка зависимостей или полная проверка и используется ли при запуске пакета 32-разрядная или 64-разрядная среда выполнения.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Создание каталога служб SSIS](ssis-catalog.md)  
  
-   [Резервное копирование, восстановление и перемещение каталога служб SSIS](../backup-restore-and-move-the-ssis-catalog.md)  
  
## <a name="related-content"></a>См. также  
  
-   Запись в блоге [Службы SSIS и Powershell в SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539)на сайте blogs.msdn.com.  
  
-   Запись в блоге [Советы по управлению доступом к каталогу служб SSIS](https://go.microsoft.com/fwlink/?LinkId=246669)на сайте blogs.msdn.com.  
  
-   Запись [Обзор модели управляемых объектов каталога служб SSIS](https://go.microsoft.com/fwlink/?LinkId=254267)в блоге blogs.msdn.com.  
  
  
