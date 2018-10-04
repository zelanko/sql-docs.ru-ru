---
title: Настройка управляемого резервного копирования (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0403d34b48b74d0517aaf3cb31ea520dbc436f89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165604"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Настройка управляемого резервного копирования (SQL Server Management Studio)
  **Управляемое резервное копирование** диалоговое окно позволяет настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] значения по умолчанию для экземпляра. В этом разделе описывается, как использовать это диалоговое окно для настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] настройки по умолчанию для экземпляра и параметры, при этом необходимо учитывать. Когда [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] настроен для экземпляра, параметры будут применены к любой новой базы данных, создаваемой в дальнейшем.  
  
 Если вы хотите настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для конкретной базы данных, см. в разделе [Включение и настройка SQL Server Managed Backup to Windows Azure для базы данных](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> Управляемое резервное копирование SQL Server не поддерживается для прокси-серверов. 
  
## <a name="task-list"></a>Список задач  
  
## <a name="includesssmartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] С помощью функции интерфейс управляемого резервного копирования в SQL Server Management Studio  
 В этом выпуске можно настроить только параметры по умолчанию уровня экземпляра, с помощью **управляемого резервного копирования** интерфейс. Не удается настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] базу данных, приостановить или возобновить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] операций или настроить уведомления по почте. Сведения о том, как выполнять операции, в настоящее время не поддерживается через **управляемое резервное копирование** интерфейсом, см. в разделе [SQL Server Managed Backup to Windows Azure — настройки хранения периода хранения и](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Разрешения  
 **Просмотр узла управляемого резервного копирования является SQL Server Management Studio:** для просмотра **управляемое резервное копирование** узел в **обозревателя объектов**, необходимо быть администратором системы или иметь следующие разрешения предоставить учетной записи пользователя:  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` на `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT` на `smart_admin.fn_backup_instance_config`.  
  
 **Настройка управляемого резервного копирования:** Настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в SQL Server Management Studio, необходимо быть системным администратором или иметь следующие разрешения:  
  
 Членство в группе `db_backupoperator` роли базы данных с помощью `ALTER ANY CREDENTIAL` разрешения, и `EXECUTE` разрешения на `sp_delete_backuphistory` хранимой процедуры.  
  
 `SELECT` разрешения на `smart_admin.fn_get_current_xevent_settings` функции.  
  
 `EXECUTE` разрешения на `smart_admin.sp_get_backup_diagnostics` хранимой процедуры. Кроме того, необходимы разрешения `VIEW SERVER STATE`, так как процедура автоматически вызывает другие системные объекты, которым требуется это разрешение.  
  
 `EXECUTE` разрешения на `smart_admin.sp_set_instance_backup`, и `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includesssmartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с помощью SQL Server Management Studio  
 Из **обозревателя объектов**, разверните **управления** узел и щелкните правой кнопкой мыши **управляемое резервное копирование**. Выберите **Настройка**. Откроется диалоговое окно **Управляемое резервное копирование** .  
  
 Проверьте **Включение управляемого резервного копирования** , укажите значения конфигурации:  
  
 **Файл хранения** период указывается в днях и должен быть от 1 до 30.  
  
 **Учетные данные SQL** вы должны соответствовать учетной записи хранения. Если в настоящее время у вас нет учетных данных SQL, в которой хранятся сведения для проверки подлинности, можно создать, перейдя по **создать**. Вы также можете создать учетные данные с помощью инструкции CREATE CREDENTIAL Transact-SQL. При этом укажите имя учетной записи хранения для удостоверения и ключ доступа для параметров SECRET. Дополнительные сведения см. в разделе [Создание учетных данных](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Укажите **URL-адрес хранилища** для учетной записи хранения Windows Azure, учетные данные SQL, в которой хранятся сведения для проверки подлинности учетной записи хранения и срок хранения для файлов резервных копий.  
  
 Формат URL-адреса хранилища: https://\<учетная запись хранения >.blob.core.windows.net/  
  
 Чтобы задать параметры шифрования на уровне экземпляра, проверьте **шифровать резервную копию** и задайте алгоритм и сертификат или асимметричный ключ, используемый для шифрования.  Эти параметры устанавливаются на уровне экземпляра и используются для всех создаваемых баз данных после применения этой конфигурации.  
  
> [!WARNING]  
>  Это диалоговое окно не может использоваться для указания параметров шифрования без настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Эти параметры шифрования применяются только к [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] операций. Чтобы использовать шифрование для других процедур резервного копирования, см. в разделе [шифрование резервной копии](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Замечания  
 Если вы настраиваете [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на уровне экземпляра, параметры будут применены к любой новой базы данных, создаваемой в дальнейшем.  Однако существующая база данных не наследует эти параметры автоматически. Чтобы настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] на ранее созданных баз данных, необходимо настроить каждую базу данных, в частности. Дополнительные сведения см. в разделе [Включение и настройка SQL Server Managed Backup to Windows Azure для базы данных](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] приостановлена с помощью `smart_admin.sp_backup_master_switch`, вы увидите предупреждение «управляемое резервное копирование отключено и текущие конфигурации не вступят в силу...» при попытке завершить настройку. Используйте `smart_admin.sp_backup_master_switch` хранятся и задать @new_state= 1. Будет возобновлена [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] службы и параметры конфигурации вступят в силу. Дополнительные сведения о хранимой процедуре, см. в разделе [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Управляемое резервное копирование SQL Server в Microsoft Azure: взаимодействие и сосуществование](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
