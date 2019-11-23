---
title: Резервное копирование в SQL Server по URL-адресу | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 11be89e9-ff2a-4a94-ab5d-27d8edf9167d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c654dc9117a8de55a3e90898487a6b9baa1d6c0d
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797998"
---
# <a name="sql-server-backup-to-url"></a>Резервное копирование в SQL Server по URL-адресу
  В этом разделе представлены основные понятия, требования и компоненты, необходимые для использования службы хранилища BLOB-объектов Azure в качестве места назначения резервного копирования. Функции резервного копирования и восстановления аналогичны при использовании DISK и TAPE, но имеют некоторые отличия. В данном разделе описаны различия и все важные исключения, а также приведено несколько примеров кода.  
  
## <a name="requirements-components-and-concepts"></a>Требования, компоненты и основные понятия  
 **В этом разделе:**  
  
-   [безопасность](#security)  
  
-   [Введение в основные компоненты и понятия](#intorkeyconcepts)  
  
-   [Служба хранилища BLOB-объектов Azure](#Blob)  
  
-   [Компоненты SQL Server](#sqlserver)  
  
-   [Ограничения](#limitations)  
  
-   [Поддержка инструкций резервного копирования и восстановления](#Support)  
  
-   [Использование задачи резервного копирования в среде SQL Server Management Studio](sql-server-backup-to-url.md#BackupTaskSSMS)  
  
-   [Резервное копирование SQL Server на URL-адрес с помощью мастера планов обслуживания](sql-server-backup-to-url.md#MaintenanceWiz)  
  
-   [Восстановление из хранилища Azure с помощью SQL Server Management Studio](sql-server-backup-to-url.md#RestoreSSMS)  
  
###  <a name="security"></a> Безопасность  
 Ниже приведены рекомендации по безопасности и требования к резервному копированию или восстановлению из служб хранилища BLOB-объектов Azure.  
  
-   При создании контейнера для службы хранилища BLOB-объектов Azure рекомендуется установить доступ к **частному**. Установка закрытых прав доступа означает, что доступ получают только те пользователи и учетные записи, которые могут предоставить необходимую информацию для проверки подлинности в учетной записи Azure.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется, чтобы имя учетной записи Azure и проверка подлинности ключей доступа хранились в учетных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти сведения используются для проверки подлинности учетной записи Azure при выполнении операций резервного копирования или восстановления.  
  
-   Учетная запись пользователя, применяемая для выдачи команды BACKUP или RESTORE, должна находиться в роли базы данных **db_backup operator** с разрешениями **Alter any credential** .  
  
###  <a name="intorkeyconcepts"></a> Введение в основные компоненты и понятия  
 В следующих двух разделах представлены службы хранилища BLOB-объектов Azure, а также компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используемые при резервном копировании или восстановлении из службы хранилища BLOB-объектов Azure. Важно понимать компоненты и взаимодействие между ними, чтобы выполнить резервное копирование или восстановление из службы хранилища BLOB-объектов Azure.  
  
 Создание учетной записи Azure является первым этапом этого процесса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует **имя учетной записи хранения Azure** и значения **ключа доступа** для проверки подлинности, записи и чтения больших двоичных объектов в службе хранилища. Учетные данные службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранят эту информацию для проверки подлинности и используются при выполнении операций резервного копирования или восстановления. Полное пошаговое руководство по созданию учетной записи хранения и выполнению простого восстановления см. в статье [руководство по использованию службы хранилища Azure для SQL Server резервного копирования и восстановления](https://go.microsoft.com/fwlink/?LinkId=271615).  
  
 ![Сопоставление учетной записи хранения с учетными данными SQL](../../tutorials/media/backuptocloud-storage-credential-mapping.gif "Сопоставление учетной записи хранения с учетными данными SQL")  
  
###  <a name="Blob"></a>Служба хранилища BLOB-объектов Azure  
 **Учетная запись хранения.** Учетная запись хранения является отправной точкой для всех служб хранилища. Чтобы получить доступ к службе хранилища BLOB-объектов Azure, сначала создайте учетную запись хранения Azure. **Имя учетной записи хранения** и ее свойства **ключа доступа** необходимы для проверки подлинности в службе хранилища BLOB-объектов Azure и ее компонентах.  
  
 **Контейнер:** Контейнер обеспечивает группирование набора больших двоичных объектов и может хранить их неограниченное количество. Чтобы записать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] резервную копию в службу BLOB-объектов Azure, необходимо создать по крайней мере корневой контейнер.  
  
 **Большой двоичный объект.** Файл любого типа и размера. Существует два типа больших двоичных объектов, которые можно хранить в службе хранилища больших двоичных объектов Azure: блочные и страничные BLOB-объекты. В резервном копировании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются страничные большие двоичные объекты. Адресация больших двоичных объектов осуществляется с помощью следующего формата URL-адреса: https://\<учетная запись хранения >. BLOB. Core. Windows. NET/\<>/\<контейнера BLOB >  
  
 ![Хранилище BLOB-объектов Azure](../../database-engine/media/backuptocloud-blobarchitecture.gif "хранилище BLOB-объектов Azure.")  
  
 Дополнительные сведения о службе хранилища BLOB-объектов Azure см. в статье [Использование службы хранилища BLOB-объектов Azure](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/) .  
  
 Дополнительную информацию о больших двоичных объектах см. в разделе [Основные сведения о блочных и страничных больших двоичных объектах](https://msdn.microsoft.com/library/windowsazure/ee691964.aspx).  
  
###  <a name="sqlserver"></a> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components  
 **URL-адрес.** URL-адрес указывает универсальный идентификатор ресурса (URI) для уникального файла резервной копии. URL-адрес используется для предоставления местоположения и имени файла резервной копии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В этой реализации единственным допустимым URL-адресом является тот, который указывает на страничный BLOB-объект в учетной записи хранения Azure. URL-адрес должен указывать на фактический большой двоичный объект, а не просто контейнер. Если большой двоичный объект не существует, он будет создан. Если указан существующий большой двоичный объект, происходит сбой резервного копирования, если не указан параметр «WITH FORMAT».  
  
> [!WARNING]  
>  Если вы решили скопировать и передать файл резервной копии в службу хранилища больших двоичных объектов Azure, используйте страничный BLOB-объект в качестве хранилища. Восстановление из блочных больших двоичных объектов не поддерживается. Попытка выполнить RESTORE из большого двоичного объекта блочного типа приводит к ошибке.  
  
 Ниже приведен пример значения URL-адреса: HTTP [s]://Аккаунтнаме.блоб.коре.Виндовс.нет/\<контейнер >/\<FILENAME. bak >. Указывать HTTPS необязательно, но рекомендуется.  
  
 **Учетные данные.** Учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] являются объектом, который используется для хранения информации о проверке подлинности, необходимой для подключения к ресурсу за пределами SQL Server.  Здесь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] процессы резервного копирования и восстановления используют учетные данные для проверки подлинности в службе хранилища BLOB-объектов Azure. Учетные данные хранят имя учетной записи хранилища и значения **ключа доступа** учетной записи хранилища. После создания учетных данных их необходимо указать в параметре WITH CREDENTIAL при выполнении инструкций BACKUP/RESTORE. Дополнительную информацию о просмотре, копировании или повторном создании учетной записи хранилища **access keys**смправа доступа. в разделе [Ключи доступа к учетной записи](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx)права доступа.  
  
 Пошаговые инструкции по созданию учетных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в примере [Создание учетных данных](#credential) далее в этом разделе.  
  
 Общие сведения об учетных данных см. в разделе [Учетные данные](../security/authentication-access/credentials-database-engine.md).  
  
 Сведения о других примерах использования учетных данных см. в разделе [Создание учетной записи-посредника агента SQL Server](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
###  <a name="limitations"></a> Ограничения  
  
-   Резервное копирование в хранилище класса Premium не поддерживается.  
  
-   Максимальный поддерживаемый размер резервной копии — 1 ТБ.  
  
-   Инструкции резервного копирования и восстановления можно выполнить с помощью TSQL, SMO и командлетов PowerShell. Резервное копирование или восстановление из службы хранилища BLOB-объектов Azure с помощью SQL Server Management Studio мастер резервного копирования или восстановления в настоящее время не включен.  
  
-   Функция создания логического имени устройства не поддерживается. Таким образом, не поддерживается функция добавления URL-адреса в качестве устройства резервного копирования с помощью sp_dumpdevice или SQL Server Management Studio.  
  
-   Функция присоединения к существующим резервным большим двоичным объектам не поддерживается. Создать резервную копию в существующем большом двоичном объекте можно только путем перезаписи с помощью параметра WITH FORMAT.  
  
-   Функция создания резервных копий в нескольких больших двоичных объектах в одной операции резервного копирования не поддерживается. К примеру, следующие действия приводят к ошибке.  
  
    ```sql
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
|BACKUP|&#x2713;|BLOCKSIZE и MAXTRANSFERSIZE не поддерживаются.|Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE|&#x2713;||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE FILELISTONLY|&#x2713;||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE HEADERONLY|&#x2713;||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE LABELONLY|&#x2713;||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE VERIFYONLY|&#x2713;||Необходимо использовать инструкцию WITH CREDENTIAL|  
|RESTORE REWINDONLY|&#x2713;|||  
  
 Общую информацию и синтаксис инструкций резервного копирования см. в разделе [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).  
  
 Общую информацию и синтаксис инструкций восстановления см. в разделе [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql).  
  
### <a name="support-for-backup-arguments"></a>Поддержка аргументов резервного копирования  
  
|||||  
|-|-|-|-|  
|Аргумент|Поддерживается|Исключение|Комментарии|  
|DATABASE|&#x2713;|||  
|LOG|&#x2713;|||  
||  
|TO (URL)|&#x2713;|В отличие от DISK и TAPE URL-адрес не поддерживает функцию указания или создания логического имени.|Этот аргумент используется, чтобы указать URL-адрес для файла резервной копии.|  
|MIRROR TO|&#x2713;|||  
|**WITH OPTIONS:**||||  
|CREDENTIAL|&#x2713;||С УЧЕТными данными поддерживается только при использовании параметра BACKUP TO URL для резервного копирования в службу хранилища BLOB-объектов Azure.|  
|DIFFERENTIAL (разностная)|&#x2713;|||  
|COPY_ONLY|&#x2713;|||  
|COMPRESSION&#124;NO_COMPRESSION|&#x2713;|||  
|Description|&#x2713;|||  
|NAME|&#x2713;|||  
|EXPIREDATE &#124; RETAINDAYS|&#x2713;|||  
|NOINIT &#124; INIT|&#x2713;||Даже если этот параметр указан, он пропускается.<br /><br /> Добавление к большим двоичным объектам невозможно. Для перезаписи резервной копии используйте аргумент FORMAT.|  
|NOSKIP &#124; SKIP|&#x2713;|||  
|NOFORMAT &#124; FORMAT|&#x2713;||Даже если этот параметр указан, он пропускается.<br /><br /> Создание резервных копий в существующем большом двоичном объекте завершается ошибкой, если не указан аргумент WITH FORMAT. Если аргумент WITH FORMAT указан, существующий большой двоичный объект будет перезаписан.|  
|MEDIADESCRIPTION|&#x2713;|||  
|MEDIANAME|&#x2713;|||  
|BLOCKSIZE|&#x2713;|||  
|BUFFERCOUNT|&#x2713;|||  
|MAXTRANSFERSIZE|&#x2713;|||  
|NO_CHECKSUM &#124; CHECKSUM|&#x2713;|||  
|STOP_ON_ERROR | CONTINUE_AFTER_ERROR|&#x2713;|||  
|STATS|&#x2713;|||  
|REWIND &#124; NOREWIND|&#x2713;|||  
|UNLOAD &#124; NOUNLOAD|&#x2713;|||  
|NORECOVERY &#124; STANDBY|&#x2713;|||  
|NO_TRUNCATE|&#x2713;|||  
  
 Дополнительные сведения об аргументах резервного копирования см. в разделе [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).  
  
### <a name="support-for-restore-arguments"></a>Поддержка аргументов восстановления  
  
|||||  
|-|-|-|-|  
|Аргумент|Поддерживается|Исключения|Комментарии|  
|DATABASE|&#x2713;|||  
|LOG|&#x2713;|||  
|FROM (URL)|&#x2713;||Аргумент FROM URL используется, чтобы указать URL-адрес для файла резервной копии.|  
|**WITH Options:**||||  
|CREDENTIAL|&#x2713;||С УЧЕТными данными поддерживается только при использовании параметра восстановить из URL-адреса для восстановления из службы хранилища больших двоичных объектов Azure.|  
|PARTIAL|&#x2713;|||  
|RECOVERY &#124; NORECOVERY &#124; STANDBY|&#x2713;|||  
|LOADHISTORY|&#x2713;|||  
|MOVE|&#x2713;|||  
|REPLACE|&#x2713;|||  
|RESTART|&#x2713;|||  
|RESTRICTED_USER|&#x2713;|||  
|FILE|&#x2713;|||  
|PASSWORD|&#x2713;|||  
|MEDIANAME|&#x2713;|||  
|MEDIAPASSWORD|&#x2713;|||  
|BLOCKSIZE|&#x2713;|||  
|BUFFERCOUNT|&#x2713;|||  
|MAXTRANSFERSIZE|&#x2713;|||  
|CHECKSUM &#124; NO_CHECKSUM|&#x2713;|||  
|STOP_ON_ERROR | CONTINUE_AFTER_ERROR|&#x2713;|||  
|FILESTREAM|&#x2713;|||  
|STATS|&#x2713;|||  
|REWIND &#124; NOREWIND|&#x2713;|||  
|UNLOAD &#124; NOUNLOAD|&#x2713;|||  
|KEEP_REPLICATION|&#x2713;|||  
|KEEP_CDC|&#x2713;|||  
|ENABLE_BROKER &#124; ERROR_BROKER_CONVERSATIONS &#124; NEW_BROKER|&#x2713;|||  
|STOPAT &#124; STOPATMARK &#124; STOPBEFOREMARK|&#x2713;|||  
  
 Дополнительные сведения об аргументах восстановления см. в разделе [Аргументы инструкции RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
##  <a name="BackupTaskSSMS"></a>Использование задачи резервного копирования в SQL Server Management Studio  
 Задача резервного копирования в SQL Server Management Studio была улучшена для включения URL-адреса в качестве одного из вариантов назначения и других вспомогательных объектов, необходимых для резервного копирования в службу хранилища Azure, например учетные данные SQL.  
  
 Следующие шаги описывают изменения, внесенные в задачу «Резервное копирование базы данных», чтобы обеспечить резервное копирование в службу хранилища Azure.  
  
1.  Запустите среду SQL Server Management Studio и подключитесь к экземпляру SQL Server.  Выберите базу данных, которую необходимо создать резервную копию, и щелкните правой кнопкой мыши **задачи**и выберите пункт **создать резервную копию..** . Откроется диалоговое окно Резервное копирование базы данных.  
  
2.  На странице Общие параметр **URL-адрес** используется для создания резервной копии в службе хранилища Azure. Если выбран этот параметр, на странице будут показаны другие параметры.  
  
    1.  **Имя файла.** Имя файла резервной копии.  
  
    2.  **Учетные данные SQL.** Можно задать существующие учетные данные SQL Server или создать новые, щелкнув пункт **Создать** рядом с полем учетных данных SQL.  
  
        > [!IMPORTANT]  
        >  В диалоговом окне, которое открывается при нажатии кнопки **Создать** , необходимо ввести сертификат управления или профиль публикации подписки. SQL Server в настоящий момент поддерживает версию 2.0 профиля публикации. Для загрузки поддерживаемой версии профиля публикации см. раздел [Загрузка профиля публикации 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
        >   
        >  Если у вас нет доступа к сертификату управления или профилю публикации, можно создать учетные данные SQL, указав имя учетной записи хранилища и сведения ключа доступа при помощи Transact-SQL или SQL Server Management Studio. Образец кода для создания учетных данных с помощью Transact-SQL см. в разделе [Создание учетных данных](#credential) . Также можно в среде SQL Server Management Studio, из экземпляра компонента database engine, щелкнуть правой кнопкой мыши **Безопасность**и выбрать пункт **Создать**, а затем **Учетные данные**. Укажите имя учетной записи хранения в поле **Идентификатор** и ключ доступа в поле **Пароль** .  
  
    3.  **Контейнер хранилища Azure:** Имя контейнера службы хранилища Azure для хранения файлов резервных копий.  
  
    4.  **Префикс URL-адреса.** Создается автоматически на основе сведений, указанных в полях, описанных на предыдущих шагах. При изменении этого значения вручную убедитесь в том, что оно соответствует прочим данным, указанным ранее. Например, при изменении URL-адреса хранения убедитесь, что учетные данные SQL заданы для проверки подлинности в той же самой учетной записи хранения.  
  
 При выборе URL-адреса в качестве назначения некоторые параметры на странице **Параметры медиа** отключаются.  Следующие разделы содержат дополнительные сведения о диалоговом окне «Резервное копирование базы данных»:  
  
 [Резервное копирование базы данных (страница "Общие")](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
 [Резервное копирование базы данных (страница "Параметры носителя")](back-up-database-media-options-page.md)  
  
 [Резервное копирование базы данных (страница "Параметры резервного копирования")](back-up-database-backup-options-page.md)  
  
 [Создание учетных данных — проверка подлинности в хранилище Azure](create-credential-authenticate-to-azure-storage.md)  
  
##  <a name="MaintenanceWiz"></a> Резервное копирование SQL Server на URL-адрес с помощью мастера планов обслуживания  
 Аналогично задаче резервного копирования, описанной выше, мастер планов обслуживания в SQL Server Management Studio был усовершенствован для включения **URL-адреса** в качестве одного из вариантов назначения и других вспомогательных объектов, необходимых для резервного копирования в службу хранилища Azure, например учетные данные SQL. Дополнительные сведения см. в разделе **Определение задач резервного копирования** статьи [Using Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure).  
  
##  <a name="RestoreSSMS"></a>Восстановление из хранилища Azure с помощью SQL Server Management Studio  
 При восстановлении базы данных **URL-адрес** включается в качестве устройства для восстановления с него. Следующие шаги описывают изменения в задаче восстановления, чтобы разрешить восстановление из хранилища Azure.  
  
1.  При выборе пункта **Устройства** на странице **Общие** задачи восстановления в SQL Server Management Studio открывается диалоговое окно **Выберите устройства резервного копирования** , где в качестве типа носителя резервной копии можно выбрать **URL-адрес** .  
  
2.  Если выбрать вариант **URL-адрес** и нажать **Добавить**, откроется диалоговое окно **Подключение к хранилищу Azure** . Укажите учетные данные SQL для проверки подлинности в службе хранилища Azure.  
  
3.  После этого SQL Server подключается к службе хранилища Azure с помощью предоставленных учетных данных SQL и открывает диалоговое окно " **Размещение файла резервной копии в Azure** ". Файлы резервной копии, находящиеся в хранилище, отобразятся на этой странице. Выберите файл, который требуется использовать для восстановления, и нажмите кнопку **ОК**. Вы вернетесь к диалоговому окну **Выберите устройства резервного копирования** , а нажав кнопку **ОК** в этом диалоговом окне — к главному диалоговому окну **Восстановить** , в котором можно будет завершить восстановление.  Дополнительные сведения см. в разделах:  
  
     [Восстановление базы данных (страница "Общие")](restore-database-general-page.md)  
  
     [Восстановление базы данных (страница "Файлы")](restore-database-files-page.md)  
  
     [Восстановление базы данных (страница "Параметры")](restore-database-options-page.md)  
  
##  <a name="Examples"></a> Примеры кода  
 В этом разделе содержатся следующие примеры.  
  
-   [Создание учетных данных](#credential)  
  
-   [Создание резервной копии всей базы данных](#complete)  
  
-   [Создание резервной копии базы данных и журнала](#databaselog)  
  
-   [Создание полной резервной копии файла первичной файловой группы](#filebackup)  
  
-   [Создание разностной резервной копии файлов первичных файловых групп](#differential)  
  
-   [Восстановление базы данных и перемещение файлов](#restoredbwithmove)  
  
-   [Восстановление состояния на определенный момент времени с помощью STOPAT](#PITR)  
  
###  <a name="credential"></a> Создание учетных данных  
 В следующем примере создаются учетные данные, в которых хранятся данные проверки подлинности службы хранилища Azure.  

   ```sql
   IF NOT EXISTS  
   (SELECT * FROM sys.credentials   
   WHERE credential_identity = 'mycredential')  
   CREATE CREDENTIAL mycredential WITH IDENTITY = 'mystorageaccount'  
   ,SECRET = '<storage access key>' ;  
   ```
  
   ```csharp
   // Connect to default sql server instance on local machine  
   Server server = new Server(".");  
   string identity = "mystorageaccount";  
   string secret = "<storage access key>";  
  
   // Create a Credential  
   string credentialName = "mycredential";  
   Credential credential = new Credential(server, credentialName);  
   credential.Create(identity, secret);  
   ```  
  
   ```powershell
   # create variables  
   $storageAccount = "mystorageaccount"  
   $storageKey = "<storage access key>"  
   $secureString = ConvertTo-SecureString $storageKey  -asplaintext -force  
   $credentialName = "mycredential"  
  
   $srvPath = "SQLSERVER:\SQL\COMPUTERNAME\INSTANCENAME"  
   # for default instance, the $srvpath variable would be "SQLSERVER:\SQL\COMPUTERNAME\DEFAULT"  
  
   # Create a credential  
   New-SqlCredential -Name $credentialName -Path $srvpath -Identity $storageAccount -Secret $secureString
   ```  
  
###  <a name="complete"></a>Резервное копирование всей базы данных  
 В следующем примере производится резервное копирование базы данных AdventureWorks2012 в службу хранилища BLOB-объектов Azure.
  
   ```sql
   BACKUP DATABASE AdventureWorks2012   
   TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012.bak'   
         WITH CREDENTIAL = 'mycredential'   
         ,COMPRESSION  
         ,STATS = 5;  
   GO
   ```  
  
   ```csharp
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
  
   ```powershell
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
  
###  <a name="databaselog"></a>Резервное копирование базы данных и журнала  
 В следующем примере используется образец базы данных AdventureWorks2012, которая по умолчанию использует простую модель восстановления. Для поддержки резервного копирования журналов база данных AdventureWorks2012 перенастраивается на использование модели полного восстановления. Затем в примере создается полная резервная копия базы данных в большом двоичном объекте Azure, а после периода обновления — резервная копия журнала. В этом примере будет создано имя резервной копии файла с меткой времени.  
  
   ```sql
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
  
   ```csharp
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

   ```powershell
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
  
###  <a name="filebackup"></a>Создание полной резервной копии файла первичной файловой группы  
 В следующем примере создается полная резервная копия файлов первичной файловой группы.
  
   ```sql
   --Back up the files in Primary:  
   BACKUP DATABASE AdventureWorks2012  
       FILEGROUP = 'Primary'  
       TO URL = 'https://mystorageaccount.blob.core.windows.net/mycontainer/AdventureWorks2012files.bck'  
       WITH CREDENTIAL = 'mycredential'  
       ,COMPRESSION;  
   GO  
   ```
  
   ```csharp
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
  
   ```powershell
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
  
###  <a name="differential"></a>Создание разностной резервной копии файлов первичной файловой группы  
 В следующем примере создается разностная резервная копия файлов первичной файловой группы.  
  
   ```sql
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
  
   ```csharp
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

   ```powershell
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
  
###  <a name="restoredbwithmove"></a>Восстановление базы данных и перемещение файлов  
 Чтобы восстановить полную резервную копию базы данных и переместить восстановленную базу данных в папку C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data, выполните следующие действия.
  
   ```sql
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
  
   ```csharp
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

   ```powershell
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
  
   ```sql
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
  
   ```csharp
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
  
   ```powershell
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
  
## <a name="see-also"></a>См. также статью  
 [Резервное копирование SQL Server на URL-адрес — рекомендации и устранение неполадок](sql-server-backup-to-url-best-practices-and-troubleshooting.md)   
 [Резервное копирование и восстановление системных баз данных (SQL Server)](back-up-and-restore-of-system-databases-sql-server.md)   
 [Учебник. SQL Server резервное копирование и восстановление в службе хранилища BLOB-объектов Azure](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
