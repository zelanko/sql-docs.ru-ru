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
ms.openlocfilehash: 021db5a2283eb6ec68ea80302e938f08e7ba1a5c
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154340"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Настройка управляемого резервного копирования (SQL Server Management Studio)
  Диалоговое окно **управляемое резервное копирование** позволяет настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] значения по умолчанию для экземпляра. В этом разделе описывается, как использовать это диалоговое окно для настройки значений [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] по умолчанию для экземпляра, а также рассматриваются параметры, которые необходимо учитывать при этом. Если для экземпляра настроен [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], параметры применяются для любой новой базы данных, создаваемой в дальнейшем.  
  
 Если вы хотите настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для конкретной базы данных, см. статью [Включение и настройка SQL Server управляемого резервного копирования в Azure для базы данных](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> Управляемое резервное копирование SQL Server не поддерживается для прокси-серверов. 
  
## <a name="task-list"></a>Список задач  
  
## <a name="includess_smartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>Функции [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], использующие интерфейс управляемого резервного копирования в SQL Server Management Studio  
 В этом выпуске можно настроить параметры по умолчанию на уровне экземпляра с помощью интерфейса **резервного копирования управления** . Невозможно настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для базы данных, приостановить или возобновить операции [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] или настроить уведомления по почте. Сведения о том, как выполнять операции, не поддерживаемые в управляемом интерфейсе **резервного копирования** , см. в разделе [SQL Server управляемое резервное копирование в Azure — параметры хранения и хранилища](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Разрешения  
 **SQL Server Management Studio Просмотреть управляемый узел резервного копирования:** Для просмотра **управляемого узла резервного копирования** в **обозревателе объектов**необходимо быть системным администратором или иметь следующие разрешения, специально предоставленные учетной записи пользователя:  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE`в `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT`в `smart_admin.fn_backup_instance_config`.  
  
 **Настройка управляемого резервного копирования:** для настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] в SQL Server Management Studio необходимо быть системным администратором или иметь следующие разрешения.  
  
 Членство в роли базы данных `db_backupoperator` с разрешениями `ALTER ANY CREDENTIAL` и разрешениями `EXECUTE` для хранимой процедуры `sp_delete_backuphistory`.  
  
 `SELECT`разрешения на `smart_admin.fn_get_current_xevent_settings` функцию.  
  
 `EXECUTE`разрешения на `smart_admin.sp_get_backup_diagnostics` хранимую процедуру. Кроме того, необходимы разрешения `VIEW SERVER STATE`, так как процедура автоматически вызывает другие системные объекты, которым требуется это разрешение.  
  
 Разрешения `EXECUTE` для `smart_admin.sp_set_instance_backup` и `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includess_smartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Настройка [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] с помощью среды SQL Server Management Studio  
 В **обозревателе объектов**разверните узел **Управление** и щелкните правой кнопкой мыши управляемое **резервное копирование**. Выберите **Настройка**. Откроется диалоговое окно **Управляемое резервное копирование** .  
  
 Установите флажок **Включить управляемое резервное копирование** и укажите значения конфигурации.  
  
 **Срок хранения файла** указывается в днях и должен находиться в диапазоне от 1 до 30.  
  
 Выбранные **учетные данные SQL** должны соответствовать учетной записи хранения. Если в настоящее время у вас нет учетных данных SQL, в которых хранятся данные проверки подлинности, можно создать ее, нажав кнопку **создать**. Вы также можете создать учетные данные с помощью инструкции CREATE CREDENTIAL Transact-SQL. При этом укажите имя учетной записи хранения для удостоверения и ключ доступа для параметров SECRET. Дополнительные сведения см. [в разделе Создание учетных данных](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Укажите **URL-адрес хранилища** для учетной записи хранения Azure, учетные данные SQL, в которых хранятся данные проверки подлинности для учетной записи хранения, а также срок хранения файлов резервной копии.  
  
 Формат URL-адреса хранилища: https://\<StorageAccount >. BLOB. Core. Windows. NET/  
  
 Чтобы задать параметры шифрования на уровне экземпляра, установите флажок **шифровать резервную копию** и укажите алгоритм и сертификат или асимметричный ключ, используемые для шифрования.  Эти параметры устанавливаются на уровне экземпляра и используются для всех создаваемых баз данных после применения этой конфигурации.  
  
> [!WARNING]  
>  Это диалоговое окно не может использоваться для указания параметров шифрования без настройки [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Эти параметры шифрования применяются только к операциям [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Чтобы использовать шифрование для других процедур резервного копирования, см. раздел [Шифрование резервной копии](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Рекомендации  
 Если для экземпляра настроен [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], параметры применяются для любой новой базы данных, создаваемой в дальнейшем.  Однако существующая база данных не наследует эти параметры автоматически. Чтобы настроить [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] для ранее созданных баз данных, необходимо отдельно настроить каждую базу данных. Дополнительные сведения см. в статье [Включение и настройка SQL Server управляемого резервного копирования в Azure для базы данных](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Если [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] работа приостановлена `smart_admin.sp_backup_master_switch`с помощью, появится предупреждение "управляемое резервное копирование отключено и текущие конфигурации не вступят в силу..." При попытке завершить настройку. Используйте хранимый параметр и @new_stateзадайте значение = 1. `smart_admin.sp_backup_master_switch` Работа служб [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] будет возобновлена, а параметры конфигурации вступят в силу. Дополнительные сведения о хранимой процедуре см. в разделе [smart_admin. sp_ &#40;BACKUP_MASTER_SWITCH Transact-&#41;SQL](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [SQL Server управляемого резервного копирования в Azure: Взаимодействие и сосуществование](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
