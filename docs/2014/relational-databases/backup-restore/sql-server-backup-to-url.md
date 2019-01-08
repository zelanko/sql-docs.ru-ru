---
title: Резервное копирование в SQL Server по URL-адресу | Документация Майкрософт
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d3911ab34a01b2da971aa602df37c8c559ed6390
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53359296"
---
# <a name="sql-server-backup-to-url"></a>Резервное копирование в SQL Server по URL-адресу
  В данном разделе представлены основные понятия, требования и компоненты, необходимые для использования службы хранилища больших двоичных объектов Windows Azure в качестве места назначения резервного копирования. Функции резервного копирования и восстановления аналогичны при использовании DISK и TAPE, но имеют некоторые отличия. В данном разделе описаны различия и все важные исключения, а также приведено несколько примеров кода.  
  
## <a name="requirements-components-and-concepts"></a>Требования, компоненты и основные понятия  
 **В этом разделе:**  
  
-   [Безопасность](#security)  
  
-   [Введение в основные компоненты и понятия](#intorkeyconcepts)  
  
-   [Windows Azure Blob Storage Service](#Blob)  
  
-   [Компоненты SQL Server](#sqlserver)  
  
-   [Ограничения](#limitations)  
  
-   [Поддержка инструкций резервного копирования и восстановления](#Support)  
  
-   [Использование задачи резервного копирования в среде SQL Server Management Studio](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [Резервное копирование SQL Server на URL-адрес с помощью мастера планов обслуживания](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [Восстановление из хранилища SQL Windows Azure с помощью среды SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a> безопасность  
 Далее описаны вопросы безопасности и требования к резервному копированию и восстановлению с помощью службы хранилища больших двоичных объектов Windows Azure.  
  
-   При создании контейнера для службы хранилища больших двоичных объектов Windows Azure рекомендуется установить для него **закрытые**права доступа. Установка закрытых прав доступа означает, что доступ предоставляется только тем пользователям и учетным записям, которые могут предоставить необходимую информацию для проверки подлинности в учетной записи Windows Azure.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требует, чтобы имя учетной записи Windows Azure и проверка подлинности ключа доступа сохранялась в учетных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта информация используется для проверки подлинности в учетной записи Windows Azure при выполнении операций резервного копирования или восстановления.  
  
-   Учетная запись пользователя, применяемая для выдачи команды BACKUP или RESTORE, должна находиться в роли базы данных **db_backup operator** с разрешениями **Alter any credential** .  
  
###  <a name="intorkeyconcepts"></a> Введение в основные компоненты и понятия  
 В следующих двух разделах описаны служба хранилища больших двоичных объектов Windows Azure, а также компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используются в момент создания резервных копий или восстановления из службы хранилища больших двоичных объектов Windows Azure. Чтобы выполнять резервное копирование или восстановление с помощью службы хранилища больших двоичных объектов Windows Azure, важно понимать компоненты и то, как они взаимосвязаны.  
  
 Создание учетной записи Windows Azure является первым этапом этого процесса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует **имя учетной записи хранения Windows Azure** и его **ключ доступа** значения для проверки подлинности и записи и чтения больших двоичных объектов службы хранилища. Учетные данные службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранят эту информацию для проверки подлинности и используются при выполнении операций резервного копирования или восстановления. Полное пошаговое руководство по созданию учетной записи для хранения и выполнения простого восстановления см. в [руководстве по использованию службы хранения Windows Azure для создания резервных копий и восстановления SQL Server](https://go.microsoft.com/fwlink/?LinkId=271615).  
  
 ![Сопоставление учетной записи хранилища с учетными данными sql](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "сопоставление учетной записи хранилища с учетными данными sql")  
  
###  <a name="Blob"></a> Windows Azure Blob Storage Service  
 **Учетная запись хранения:** Учетная запись хранилища является отправной точкой для всех служб хранилища. Для доступа к службе хранилища больших двоичных объектов Windows Azure необходимо сначала создать учетную запись хранилища Windows Azure. Для проверки подлинности в службе хранилища больших двоичных объектов Windows Azure и его компонентах необходимы **storage account name** и его свойства **access key** .  
  
 **Контейнер:** Контейнер обеспечивает группирование набора больших двоичных объектов и может хранить их неограниченное количество. Для создания резервных копий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в службе хранилища больших двоичных объектов Windows Azure необходимо как минимум создать корневой контейнер.  
  
 **BLOB-объектов:** Файл любого типа и размера. Существуют два типа больших двоичных объектов, которые можно хранить в службе хранилища BLOB- объектов Windows Azure: блочные и страничные BLOB-объекты. В резервном копировании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются страничные большие двоичные объекты. Большие двоичные объекты можно обратиться, используя следующий формат URL-адрес: https://\<учетной записи хранения >.blob.core.windows.net/\<контейнер > /\<большого двоичного объекта >  
  
 ![Хранилище BLOB-объектов Azure](../../database-engine/media/backuptocloud-blobarchitecture.gif "Хранилище BLOB-объектов Azure")  
  
 Дополнительную информацию о службе хранилища больших двоичных объектов Windows Azure см. в разделе [Как использовать службу хранилища больших двоичных объектов Windows Azure](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Дополнительную информацию о больших двоичных объектах см. в разделе [Основные сведения о блочных и страничных больших двоичных объектах](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx).  
  
###  <a name="sqlserver"></a> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components  
 **URL-АДРЕС:** URL-адрес указывает универсальный идентификатор ресурса (URI) для уникального файла резервной копии. URL-адрес используется для предоставления местоположения и имени файла резервной копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В этой реализации единственным допустимым URL-адресом является тот, который указывает на страничный большой двоичный объект в учетной записи хранилища Windows Azure. URL-адрес должен указывать на фактический большой двоичный объект, а не просто контейнер. Если большой двоичный объект не существует, он будет создан. Если существующий большой двоичный объект указанного резервного КОПИРОВАНИЯ завершается ошибкой, если не указан параметр «WITH FORMAT».  
  
> [!WARNING]  
>  При копировании и загрузке файла резервной копии в службу хранилища больших двоичных объектов Windows Azure используйте в качестве хранилища большой двоичный объект страничного типа. Восстановление из блочных больших двоичных объектов не поддерживается. Попытка выполнить RESTORE из большого двоичного объекта блочного типа приводит к ошибке.  
  
 Ниже приведен пример значение URL-адреса: http[s]://ACCOUNTNAME.Blob.core.windows.net/\<КОНТЕЙНЕР > /\<FILENAME.bak >. Указывать HTTPS необязательно, но рекомендуется.  
  
 **Учетные данные.** Учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] являются объектом, который используется для хранения информации о проверке подлинности, которая необходима для подключения к источнику за пределами SQL Server.  В данном случае процессы резервного копирования и восстановления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют учетные данные для проверки подлинности в службе хранилища больших двоичных объектов Windows Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительную информацию о просмотре, копировании или повторном создании учетной записи хранилища **access keys**смправа доступа. в разделе [Ключи доступа к учетной записи](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)права доступа.  
  
 Пошаговые инструкции по созданию учетных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в примере [Create a Credential](#credential) далее в этом разделе.  
  
 Общие сведения об учетных данных см. в разделе [Учетные данные](../security/authentication-access/credentials-database-engine.md).  
  
 Сведения о других примерах использования учетных данных см. в разделе [Создание учетной записи-посредника агента SQL Server](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
###  <a name="limitations"></a> Ограничения  
  
-   Резервное копирование в хранилище класса Premium не поддерживается.  
  
-   Максимальный поддерживаемый размер резервной копии — 1 ТБ.  
  
-   Инструкции резервного копирования и восстановления можно выполнить с помощью TSQL, SMO и командлетов PowerShell. Функция резервного копирования или восстановления из службы хранилища больших двоичных объектов Windows Azure с помощью мастера резервного копирования или восстановления среды SQL Server Management Studio на данный момент не включена.  
  
-   Функция создания логического имени устройства не поддерживается. Таким образом, не поддерживается функция добавления URL-адреса в качестве устройства резервного копирования с помощью sp_dumpdevice или SQL Server Management Studio.  
  
-   Функция присоединения к существующим резервным большим двоичным объектам не поддерживается. Создать резервную копию в существующем большом двоичном объекте можно только путем перезаписи с помощью параметра WITH FORMAT.  
  
-   Функция создания резервных копий в нескольких больших двоичных объектах в одной операции резервного копирования не поддерживается. К примеру, следующие действия приводят к ошибке.  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_1.bak'   
       URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_2.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,STATS = 5;  
    GO  
  
    ```  
  
-   Функция указания размера блока с помощью `BACKUP` не поддерживается.  
  
-   Функция указания `MAXTRANSFERSIZE` не поддерживается.  
  
-   Указание набора параметров резервного набора данных `RETAINDAYS` и `EXPIREDATE` не поддерживается.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — 259 символов. Функция BACKUP TO URL использует 36 символов для необходимых элементов, которые нужны для указания URL (https://.blob.core.windows.net//.bak), оставляя 223 символа для имен учетной записи, контейнера и большого двоичного объекта.  
  
###  <a name="Support"></a> Поддержка инструкций резервного копирования и восстановления  
  
|||||  
|-|-|-|-|  
|Инструкции BACKUP и RESTORE|Поддерживается|Исключения|Комментарии|  
|BACKUP|???|BLOCKSIZE и MAXTRANSFERSIZE не поддерживаются.|Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE|???||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE FILELISTONLY|???||Необходимо использовать инструкцию WITH CREDENTIAL|  
|инструкция RESTORE HEADERONLY|???||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE LABELONLY|???||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE VERIFYONLY|???||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE REWINDONLY|???|||  
  
 Общую информацию и синтаксис инструкций резервного копирования см. в разделе [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).  
  
 Общую информацию и синтаксис инструкций восстановления см. в разделе [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql).  
  
### <a name="support-for-backup-arguments"></a>Поддержка аргументов резервного копирования  
  
|||||  
|-|-|-|-|  
|Аргумент|Поддерживается|Исключение|Комментарии|  
|DATABASE|???|||  
|LOG|???|||  
||  
|TO (URL)|???|В отличие от DISK и TAPE URL-адрес не поддерживает функцию указания или создания логического имени.|Этот аргумент используется, чтобы указать URL-адрес для файла резервной копии.|  
|MIRROR TO|???|||  
|**WITH OPTIONS:**||||  
|CREDENTIAL|???||Функция WITH CREDENTIAL поддерживается только при использовании параметра BACKUP TO URL для резервного копирования с помощью службы хранилища больших двоичных объектов Windows Azure.|  
|DIFFERENTIAL (разностная)|???|||  
|COPY_ONLY|???|||  
|COMPRESSION&#124;NO_COMPRESSION|???|||  
|DESCRIPTION|???|||  
|NAME|???|||  
|EXPIREDATE &#124; RETAINDAYS|???|||  
|NOINIT &#124; INIT|???||Даже если этот параметр указан, он пропускается.<br /><br /> Добавление к большим двоичным объектам невозможно. Для перезаписи резервной копии используйте аргумент FORMAT.|  
|NOSKIP &#124; SKIP|???|||  
|NOFORMAT &#124; FORMAT|???||Даже если этот параметр указан, он пропускается.<br /><br /> Создание резервных копий в существующем большом двоичном объекте завершается ошибкой, если не указан аргумент WITH FORMAT. Если аргумент WITH FORMAT указан, существующий большой двоичный объект будет перезаписан.|  
|MEDIADESCRIPTION|???|||  
|MEDIANAME|???|||  
|BLOCKSIZE|???|||  
|BUFFERCOUNT|???|||  
|MAXTRANSFERSIZE|???|||  
|NO_CHECKSUM &#124; CHECKSUM|???|||  
|STOP_ON_ERROR | CONTINUE_AFTER_ERROR|???|||  
|STATS|???|||  
|REWIND &#124; NOREWIND|???|||  
|UNLOAD &#124; NOUNLOAD|???|||  
|NORECOVERY &#124; STANDBY|???|||  
|NO_TRUNCATE|???|||  
  
 Дополнительные сведения об аргументах резервного копирования см. в разделе [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).  
  
### <a name="support-for-restore-arguments"></a>Поддержка аргументов восстановления  
  
|||||  
|-|-|-|-|  
|Аргумент|Поддерживается|Исключения|Комментарии|  
|DATABASE|???|||  
|LOG|???|||  
|FROM (URL)|???||Аргумент FROM URL используется, чтобы указать URL-адрес для файла резервной копии.|  
|**WITH Options:**||||  
|CREDENTIAL|???||Функция WITH CREDENTIAL поддерживается только при использовании параметра RESTORE FROM URL для восстановления из службы хранилища больших двоичных объектов Windows Azure.|  
|PARTIAL|???|||  
|RECOVERY &#124; NORECOVERY &#124; STANDBY|???|||  
|LOADHISTORY|???|||  
|MOVE|???|||  
|REPLACE|???|||  
|RESTART|???|||  
|RESTRICTED_USER|???|||  
|FILE|???|||  
|PASSWORD|???|||  
|MEDIANAME|???|||  
|MEDIAPASSWORD|???|||  
|BLOCKSIZE|???|||  
|BUFFERCOUNT|???|||  
|MAXTRANSFERSIZE|???|||  
|CHECKSUM &#124; NO_CHECKSUM|???|||  
|STOP_ON_ERROR | CONTINUE_AFTER_ERROR|???|||  
|FILESTREAM|???|||  
|STATS|???|||  
|REWIND &#124; NOREWIND|???|||  
|UNLOAD &#124; NOUNLOAD|???|||  
|KEEP_REPLICATION|???|||  
|KEEP_CDC|???|||  
|ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER|???|||  
|STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK|???|||  
  
 Дополнительные сведения об аргументах восстановления см. в разделе [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
##  <a name="BackupTaskSSMS"></a> Использование задачи резервного копирования в SQL Server Management Studio  
 Задача резервного копирования в SQL Server Management Studio расширена и включает URL-адрес как один из вариантов места назначения, а также другие вспомогательные объекты, необходимые для резервного копирования в хранилище Windows Azure, такие как учетные данные SQL.  
  
 Следующие шаги описывают изменения, внесенные в задачу «резервное копирование базы данных» для создания резервной копии в хранилище Windows Azure.  
  
1.  Запустите среду SQL Server Management Studio и подключитесь к экземпляру SQL Server.  Выберите базу данных для резервного копирования и щелкните правой кнопкой мыши **задачи**и выберите **резервного копирования...** . Откроется диалоговое окно «Резервное копирование базы данных».  
  
2.  Параметр **URL-адрес** на общей странице используется для создания резервной копии в хранилище Windows Azure. Если выбран этот параметр, на странице будут показаны другие параметры.  
  
    1.  **Имя файла:** Имя файла резервной копии.  
  
    2.  **Учетные данные SQL.** Можно задать существующие учетные данные SQL Server, или можно создать новую, щелкнув **создать** рядом с полем учетных данных SQL.  
  
        > [!IMPORTANT]  
        >  В диалоговом окне, которое открывается при нажатии кнопки **Создать** , необходимо ввести сертификат управления или профиль публикации подписки. SQL Server в настоящий момент поддерживает версию 2.0 профиля публикации. Для загрузки поддерживаемой версии профиля публикации см. раздел [Загрузка профиля публикации 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
        >   
        >  Если у вас нет доступа к сертификату управления или профилю публикации, можно создать учетные данные SQL, указав имя учетной записи хранилища и сведения ключа доступа при помощи Transact-SQL или SQL Server Management Studio. Образец кода для создания учетных данных с помощью Transact-SQL см. в разделе [Создание учетных данных](#credential) . Также можно в среде SQL Server Management Studio, из экземпляра компонента database engine, щелкнуть правой кнопкой мыши **Безопасность**и выбрать пункт **Создать**, а затем **Учетные данные**. Укажите имя учетной записи хранения в поле **Идентификатор** и ключ доступа в поле **Пароль** .  
  
    3.  **Контейнер хранилища Azure.** Имя контейнера хранилища Windows Azure для хранения файлов резервной копии.  
  
    4.  **Префикс URL-адреса:** Создается автоматически на основе сведений, указанных в полях, описанных на предыдущих шагах. При изменении этого значения вручную убедитесь в том, что оно соответствует прочим данным, указанным ранее. Например, при изменении URL-адреса хранения убедитесь, что учетные данные SQL заданы для проверки подлинности в той же самой учетной записи хранения.  
  
 При выборе URL-адреса в качестве назначения некоторые параметры на странице **Параметры медиа** отключаются.  Следующие разделы содержат дополнительные сведения о диалоговом окне «Резервное копирование базы данных»:  
  
 [Резервное копирование базы данных (страница "Общие")](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [Резервное копирование базы данных (страница "Параметры носителя")](back-up-database-media-options-page.md)  
  
 [Резервное копирование базы данных (страница "Параметры резервного копирования")](back-up-database-backup-options-page.md)  
  
 [Создание учетных данных — проверка подлинности в хранилище Azure](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="MaintenanceWiz"></a> Резервное копирование SQL Server на URL-адрес с помощью мастера планов обслуживания  
 Аналогично задаче резервного копирования, описанной выше, мастер планов обслуживания в SQL Server Management Studio расширен и включает **URL** как один из вариантов места назначения, а также другие вспомогательные объекты, необходимые для резервного копирования в хранилище Windows Azure, такие как учетные данные SQL. Дополнительные сведения см. в разделе **Определение задач резервного копирования** статьи [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).  
  
##  <a name="RestoreSSMS"></a> Восстановление из хранилища Windows Azure с помощью SQL Server Management Studio  
 При восстановлении базы данных **URL-адрес** включается в качестве устройства для восстановления с него. Следующие шаги описывают изменения в задаче восстановления, разрешающие восстановление из хранилища Windows Azure.  
  
1.  При выборе пункта **Устройства** на странице **Общие** задачи восстановления в SQL Server Management Studio открывается диалоговое окно **Выберите устройства резервного копирования** , где в качестве типа носителя резервной копии можно выбрать **URL-адрес** .  
  
2.  Если выбрать вариант **URL-адрес** и нажать **Добавить**, откроется диалоговое окно **Подключение к хранилищу Azure** . Укажите учетные данные SQL, используемые для проверки подлинности в хранилище Windows Azure.  
  
3.  SQL Server подключится к хранилищу Windows Azure с помощью предоставленных учетных данных SQL и откроет диалоговое окно **Поиск файла резервной копии в Windows Azure** . Файлы резервной копии, находящиеся в хранилище, отобразятся на этой странице. Выберите файл, который требуется использовать для восстановления, и нажмите кнопку **ОК**. Вы вернетесь к диалоговому окну **Выберите устройства резервного копирования** , а нажав кнопку **ОК** в этом диалоговом окне — к главному диалоговому окну **Восстановить** , в котором можно будет завершить восстановление.  Дополнительные сведения см. в разделах:  
  
     [Восстановление базы данных (страница "Общие")](restore-database-general-page.md)  
  
     [Восстановление базы данных (страница "Файлы")](restore-database-files-page.md)  
  
     [Восстановление базы данных (страница "Параметры")](restore-database-options-page.md)  
  
##  <a name="Examples"></a> Примеры кода  
 В этом разделе содержатся следующие примеры.  
  
-   [Создание учетных данных](#credential)  
  
-   [Создание резервной копии всей базы данных](#complete)  
  
-   [Создание резервной копии базы данных и журнала](#databaselog)  
  
-   [Создание полной резервной копии первичной файловой группы](#filebackup)  
  
-   [Создание разностной резервной копии файлов первичных файловых групп](#differential)  
  
-   [Восстановление базы данных и перемещение файлов](#restoredbwithmove)  
  
-   [Восстановление состояния на определенный момент времени с помощью STOPAT](#PITR)  
  
###  <a name="credential"></a> Создание учетных данных  
 В следующем примере создаются учетные данные для хранения сведений о проверке подлинности информации хранилища Windows Azure.  
  
1.  **tsql**  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key>' ;  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
    string secret = "<storage access key>";  
  
    // Create a Credential  
    string credentialName = "mycredential";  
    Credential credential = new Credential(server, credentialName);  
    credential.Create(identity, secret);  
    ```  
  
3.  **PowerShell**  
  
    ```  
    # create variables  
    $storageAccount = "mystorageaccount"  
    $storageKey = "<storage access key>"  
    $secureString = convertto-securestring $storageKey  -asplaintext -force  
    $credentialName = "mycredential"  
  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Create a credential  
     New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString  
  
    ```  
  
###  <a name="complete"></a> Резервное копирование всей базы данных  
 Следующий пример производит резервное копирование базы данных AdventureWorks2012 в службу хранилища больших двоичных объектов Windows Azure.  
  
1.  **tsql**  
  
    ```  
    BACKUP DATABASE AdventureWorks2012   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
          WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
    GO  
  
    ```  
  
1.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
    ```  
  
2.  **PowerShell**  
  
    ```  
    # create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"   
    # for default instance, the $srvpath varilable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
    CD $srvPath   
    $backupFile = $backupUrlContainer + "AdventureWorks2012" +  ".bak"  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On  
  
    ```  
  
###  <a name="databaselog"></a> Резервное копирование базы данных и журнала  
 В следующем примере используется образец базы данных AdventureWorks2012, которая по умолчанию использует простую модель восстановления. Для поддержки резервного копирования журналов база данных AdventureWorks2012 перенастраивается на использование модели полного восстановления. Затем выполняется полное резервное копирование базы данных в большой двоичный объект Windows Azure и после обновления — резервное копирование журнала. В этом примере будет создано имя резервной копии файла с меткой времени.  
  
1.  **tsql**  
  
    ```  
    -- To permit log backups, before the full database backup, modify the database   
    -- to use the full recovery model.  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks2012  
       SET RECOVERY FULL;  
    GO  
  
    -- Back up the full AdventureWorks2012 database.  
           -- First create a file name for the backup file with DateTime stamp  
  
    DECLARE @Full_Filename AS VARCHAR (300);  
    SET @Full_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Full_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.bak';   
    --Back up Adventureworks2012 database  
  
    BACKUP DATABASE AdventureWorks2012  
    TO URL =  @Full_Filename  
    WITH CREDENTIAL = 'mycredential';  
    ,COMPRESSION  
    GO  
    -- Back up the AdventureWorks2012 log.  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url for data backup  
    string urlDataBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Data-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database to Url  
    Backup backupData = new Backup();  
    backupData.CredentialName = credentialName;  
    backupData.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupData.Devices.AddDevice(urlDataBackup, DeviceType.Url);  
    backupData.SqlBackup(server);  
  
    // Generate Unique Url for data backup  
    string urlLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}_Log-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Database Log to Url  
    Backup backupLog = new Backup();  
    backupLog.CredentialName = credentialName;  
    backupLog.Database = dbName;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backupLog.Devices.AddDevice(urlLogBackup, DeviceType.Url);  
    backupLog.Action = BackupActionType.Log;  
    backupLog.SqlBackup(server);  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to theSQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the full database backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Backup Database to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Database    
  
    #Create a unique file name for log backup  
  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup Log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Log  
  
    ```  
  
###  <a name="filebackup"></a> Создание полной резервной копии первичной файловой группы  
 В следующем примере создается полная резервная копия файлов первичной файловой группы.  
  
1.  **tsql**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bck",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to the SQL Server Instance  
  
    CD $srvPath   
    #Create a unique file name for the file backup  
    $backupFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bck"  
  
    #Backup Primary File Group to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary  
  
    ```  
  
###  <a name="differential"></a> Создание разностной резервной копии файлов первичной файловой группы  
 В следующем примере создается разностная резервная копия файлов первичной файловой группы.  
  
1.  **tsql**  
  
    ```  
    --Back up the files in Primary:  
    BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012filesdiff.bck'  
       WITH   
          CREDENTIAL = 'mycredential'  
          ,COMPRESSION  
      ,DIFFERENTIAL;  
    GO  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string url = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Action = BackupActionType.Files;  
    backup.DatabaseFileGroups.Add("PRIMARY");  
    backup.Incremental = true;  
    backup.CompressionOption = BackupCompressionOptions.On;  
    backup.Devices.AddDevice(url, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    #Create a differential backup of the primary filegroup  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName -CompressionOption On -BackupAction Files -DatabaseFileGroup Primary -Incremental  
  
    ```  
  
###  <a name="restoredbwithmove"></a> Восстановление базы данных и перемещение файлов  
 Чтобы восстановить полную резервную копию базы данных и переместить восстановленную базу данных в папку C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data, выполните следующие действия.  
  
1.  **tsql**  
  
    ```  
    -- Backup the tail of the log first  
  
    DECLARE @Log_Filename AS VARCHAR (300);  
    SET @Log_Filename = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012_Log_'+   
    REPLACE (REPLACE (REPLACE (CONVERT (VARCHAR (40), GETDATE (), 120), '-','_'),':', '_'),' ', '_') + '.trn';  
    BACKUP LOG AdventureWorks2012  
     TO URL = @Log_Filename  
    WITH CREDENTIAL = 'mycredential'  
    ,NORECOVERY;  
    GO  
  
    RESTORE DATABASE AdventureWorks2012 FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'  
    WITH CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,MOVE 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,STATS = 5  
  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for tail log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath  + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName+ "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTNACENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # navigate to SQL Server Instance   
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On      
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery    
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath)  
  
    ```  
  
###  <a name="PITR"></a> Восстановление состояния на определенный момент времени с помощью STOPAT  
 В следующем примере производится восстановление базы данных к состоянию на определенный момент времени и демонстрируется операция восстановления.  
  
1.  **tsql**  
  
    ```  
    RESTORE DATABASE AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
    WITH   
     CREDENTIAL = 'mycredential'  
    ,MOVE 'AdventureWorks2012_data' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf'  
    ,Move 'AdventureWorks2012_log' to 'C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf'  
    ,NORECOVERY  
    --,REPLACE  
    ,STATS = 5;  
    GO   
  
    RESTORE LOG AdventureWorks FROM URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.trn'   
    WITH CREDENTIAL = 'mycredential'  
    ,RECOVERY   
    ,STOPAT = 'Oct 23, 2012 5:00 PM'   
    GO  
    ```  
  
2.  **C#**  
  
    ```  
    // Connect to default sql server instance on local machine  
    Server server = new Server(".");  
    string identity = "mystorageaccount";  
  
    string credentialName = "mycredential";  
    string dbName = "AdventureWorks2012";  
    string blobContainerName = "mycontainer";  
  
    // Generate Unique Url  
    string urlBackupData = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-Data{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup to Url  
    Backup backup = new Backup();  
    backup.CredentialName = credentialName;  
    backup.Database = dbName;  
    backup.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    backup.SqlBackup(server);  
  
    // Generate Unique Url for Tail Log backup  
    string urlTailLogBackup = String.Format(@"https://{0}.blob.core.windows.net/{1}/{2}-TailLog{3}.bak",  
            identity,  
            blobContainerName,  
            dbName,  
            DateTime.Now.ToString("s").Replace(":", "-"));  
  
    // Backup Tail Log to Url  
    Backup backupTailLog = new Backup();  
    backupTailLog.CredentialName = credentialName;  
    backupTailLog.Database = dbName;  
    backupTailLog.Action = BackupActionType.Log;  
    backupTailLog.NoRecovery = true;  
    backupTailLog.Devices.AddDevice(urlTailLogBackup, DeviceType.Url);  
    backupTailLog.SqlBackup(server);  
  
    // Restore a database and move files  
    string newDataFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".mdf";  
    string newLogFilePath = server.MasterDBLogPath + @"\" + dbName + DateTime.Now.ToString("s").Replace(":", "-") + ".ldf";  
  
    Restore restore = new Restore();  
    restore.CredentialName = credentialName;  
    restore.Database = dbName;  
    restore.ReplaceDatabase = true;  
    restore.NoRecovery = true;  
    restore.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restore.RelocateFiles.Add(new RelocateFile(dbName, newDataFilePath));  
    restore.RelocateFiles.Add(new RelocateFile(dbName + "_Log", newLogFilePath));  
    restore.SqlRestore(server);  
  
    // Restore transaction Log with stop at   
    Restore restoreLog = new Restore();  
    restoreLog.CredentialName = credentialName;  
    restoreLog.Database = dbName;  
    restoreLog.Action = RestoreActionType.Log;  
    restoreLog.Devices.AddDevice(urlBackupData, DeviceType.Url);  
    restoreLog.ToPointInTime = DateTime.Now.ToString();   
    restoreLog.SqlRestore(server);  
  
    ```  
  
3.  **PowerShell**  
  
    ```  
  
    #create variables  
    $backupUrlContainer = "https://mystorageaccount.blob.core.windows.net/mycontainer/"  
    $credentialName = "mycredential"  
    $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
    # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
    # Navigate to SQL Server Instance Directory  
  
    CD $srvPath   
  
    #create a unique file name for the full backup  
    $backupdbFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".bak"  
  
    # Full database backup to URL  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupdbFile  -SqlCredential $credentialName -CompressionOption On     
  
    #Create a unique file name for the tail log backup  
    $backuplogFile = $backupUrlContainer + "AdventureWorks2012_" + (Get-Date).ToString("s").Replace("-","_").Replace(":", "_").Replace(" ","_").Replace("/", "_") +  ".trn"  
  
    #Backup tail log to URL  
  
    Backup-SqlDatabase -Database AdventureWorks2012 -backupFile $backupFile  -SqlCredential $credentialName  -BackupAction Log -NoRecovery     
  
    # Restore Database and move files  
  
    $newDataFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile ("AdventureWorks_Data","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.mdf")  
    $newLogFilePath = New-Object Microsoft.SqlServer.Management.Smo.RelocateFile("AdventureWorks_Log","C:\Program Files\Microsoft SQL Server\myinstance\MSSQL\DATA\AdventureWorks2012.ldf")  
  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backupdbFile -RelocateFile @($newDataFilePath,$newLogFilePath) -NoRecovery    
  
    # Restore Transaction log with Stop At:  
    Restore-SqlDatabase -Database AdventureWorks2012 -SqlCredential $credentialName -BackupFile $backuplogFile  -ToPointInTime (Get-Date).ToString()  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Резервное копирование и восстановление системных баз данных (SQL Server)](back-up-and-restore-of-system-databases-sql-server.md)   
 [Учебник. SQL Server Backup and Restore для Windows Azure Blob Storage Service](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
  
