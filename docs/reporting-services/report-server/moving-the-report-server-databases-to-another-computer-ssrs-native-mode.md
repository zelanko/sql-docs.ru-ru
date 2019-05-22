---
title: Перемещение баз данных сервера отчетов на другой компьютер (службы SSRS в собственном режиме) | Документы Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 44a9854d-e333-44f6-bdc7-8837b9f34416
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: be1e4f34356f611e4c76ba57aa12bd13b0bf8f30
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65619681"
---
# <a name="moving-the-report-server-databases-to-another-computer-ssrs-native-mode"></a>Перемещение баз данных сервера отчетов на другой компьютер (собственный режим служб SSRS)

  Базы данных сервера отчетов, используемые при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], можно переместить в экземпляр на другом компьютере. Базы данных reportserver и reportservertempdb должны перемещаться или копироваться вместе. Установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует наличия обеих баз данных. База данных reportservertempdb должна быть связана по имени с перемещаемой базой данных reportserver.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.  
  
 Перемещение базы данных не влияет на запланированные операции, определенные в данный момент для элементов сервера отчетов.  
  
-   Расписания будут созданы повторно при первом перезапуске службы сервера отчетов.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующиеся для запуска расписания, будут созданы повторно в новом экземпляре базы данных. Необязательно перемещать эти задания на новый компьютер, однако следует удалить задания на компьютере, на котором они больше не будут использоваться.  
  
-   Подписки, кэшированные отчеты и моментальные снимки сохраняются в перемещенной базе данных. Если после перемещения базы данных моментальный снимок не принимает обновленные данные, очистите параметры моментального снимка и выберите **Применить**, чтобы сохранить изменения, а затем повторно создайте расписание и вновь сохраните изменения, выбрав **Применить**.  
  
-   Временные данные отчета и пользовательского сеанса, хранящиеся в базе данных reportservertempdb, при перемещении этой базы данных сохраняются.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предусматривает несколько подходов к перемещению баз данных, включая резервное копирование и восстановление, присоединение и отсоединение, а также копирование. Не все из них пригодны для переноса существующей базы данных на новый экземпляр сервера. Подход, который следует использовать для перемещения базы данных сервера отчетов, зависит от требований к доступности системы. Наиболее простой способ перемещения баз данных сервера отчетов состоит в их отсоединении и присоединении. Однако такой подход требует, чтобы сервер отчетов во время отсоединения базы данных был переведен в режим «вне сети». Если нужно свести к минимуму перерывы в обслуживании, лучшим выбором будет резервное копирование и восстановление, хотя для выполнения этих операций потребуется запуск команд [!INCLUDE[tsql](../../includes/tsql-md.md)] . Не рекомендуется выполнять копирование базы данных (особенно с помощью мастера копирования базы данных), так как при этом в базе данных не сохраняются настройки разрешений.  
  
> [!IMPORTANT]  
>  Приведенные в статье шаги рекомендуется применять, когда перемещение базы данных сервера отчетов является единственным изменением, вносимым в текущую установку. При миграции всей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (то есть для перемещения базы данных и изменения удостоверения службы Windows сервера отчетов, которая использует эту базу данных) необходима повторная настройка соединения и сброс ключа шифрования.  
  
## <a name="detaching-and-attaching-the-report-server-databases"></a>Отсоединение и присоединение баз данных сервера отчетов  
 Если сервер отчетов может быть переведен в режим «вне сети», можно отсоединить базы данных, чтобы переместить их на тот экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который требуется использовать. При таком подходе разрешения в базах данных сохраняются. Если используется база данных SQL Server, необходимо переместить ее на другой экземпляр SQL Server. После перемещения баз данных следует заново настроить соединение сервера отчетов с базой данных сервера отчетов. Если при масштабном развертывании запущено несколько серверов отчетов, необходимо заново настроить подключение к базе данных сервера отчетов для каждого сервера отчетов, входящего в конфигурацию.  
  
 Для перемещения баз данных выполните следующие шаги:  
  
1.  Создайте резервную копию ключей шифрования для перемещаемой базы данных. Для этого можно использовать программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Остановите службу сервера отчетов. Для этого можно использовать программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
3.  Запустите среду [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и установите соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором находятся базы данных сервера отчетов.  
  
4.  Щелкните правой кнопкой мыши базу данных сервера отчетов, укажите пункт "Задачи" и выберите команду **Отсоединить**. Повторите этот шаг для временной базы данных сервера отчетов.  
  
5.  Скопируйте или переместите MDF- и LDF-файлы в папку данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который необходимо использовать. Поскольку осуществляется перемещение двух баз данных, удостоверьтесь, что скопированы или перемещены все четыре файла.  
  
6.  В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]установите соединение с новым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором будут размещены базы данных сервера отчетов.  
  
7.  Щелкните правой кнопкой мыши узел "Базы данных" и выберите пункт **Присоединить**.  
  
8.  Нажмите кнопку **Добавить** , чтобы выбрать MDF- и LDF-файлы базы данных сервера отчетов, которые следует присоединить. Повторите этот шаг для временной базы данных сервера отчетов.  
  
9. После присоединения баз данных удостоверьтесь, что роль **RSExecRole** представляет собой роль базы данных как в базе данных, так и во временной базе данных сервера отчетов. Роль**RSExecRole** должна иметь разрешения на выбор, вставку, обновление, удаление и ссылку на таблицы базы данных сервера отчетов и разрешения на выполнение хранимых процедур. Дополнительные сведения см. в разделе [Создание RSExecRole](../../reporting-services/security/create-the-rsexecrole.md).  
  
10. Запустите программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и соединитесь с сервером отчетов.  
  
11. На странице «База данных» выберите новый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и нажмите кнопку **Соединить**.  
  
12. Выберите вновь перемещенную базу данных сервера отчетов и нажмите кнопку **Применить**.  
  
13. На странице «Ключи шифрования» нажмите кнопку «Восстановить». Укажите файл, содержащий резервную копию ключей и пароль для разблокирования этого файла.  
  
14. Перезапустите службу сервера отчетов.  
  
## <a name="backing-up-and-restoring-the-report-server-databases"></a>Резервное копирование и восстановление из копии баз данных сервера отчетов  
 Если сервер отчетов нельзя перевести в режим «вне сети», для перемещения его баз данных можно использовать резервное копирование и восстановление. Чтобы выполнить резервное копирование и восстановление, необходимо использовать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . После восстановления баз данных следует настроить сервер отчетов, чтобы он использовал базу данных на новом экземпляре сервера. Дополнительные сведения см. в инструкциях, приведенных в конце этого подраздела.  
  
### <a name="using-backup-and-copyonly-to-backup-the-report-server-databases"></a>Использование для резервного копирования баз данных сервера отчетов инструкций BACKUP и COPY_ONLY  
 При резервном копировании баз данных установите аргумент COPY_ONLY. Убедитесь, что создаются резервные копии как баз данных, так и файлов журналов.  
  
```  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServer  
   SET RECOVERY FULL  
  
-- If the ReportServerData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerData',   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\BACKUP\ReportServerData.bak'  
  
-- Create a logical backup device, ReportServerLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\BACKUP\ReportServerLog.bak'  
  
-- Back up the full ReportServer database.  
BACKUP DATABASE ReportServer  
   TO ReportServerData  
   WITH COPY_ONLY  
  
-- Back up the ReportServer log.  
BACKUP LOG ReportServer  
   TO ReportServerLog  
   WITH COPY_ONLY  
  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServerTempdb  
   SET RECOVERY FULL  
  
-- If the ReportServerTempDBData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBData',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBData.bak'  
  
-- Create a logical backup device, ReportServerTempDBLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBLog.bak'  
  
-- Back up the full ReportServerTempDB database.  
BACKUP DATABASE ReportServerTempDB  
   TO ReportServerTempDBData  
   WITH COPY_ONLY  
  
-- Back up the ReportServerTempDB log.  
BACKUP LOG ReportServerTempDB  
   TO ReportServerTempDBLog  
   WITH COPY_ONLY  
```  
  
### <a name="using-restore-and-move-to-relocate-the-report-server-databases"></a>Использование для перемещения баз данных сервера отчетов инструкций RESTORE и MOVE  
 При восстановлении баз данных из копии обязательно включите аргумент MOVE, чтобы можно было указать путь. Для первоначального восстановления используйте аргумент NORECOVERY, это позволяет сохранить базу данных в состоянии RESTORING и даст время для просмотра резервных копий журналов, чтобы определить, какой из них следует восстанавливать. В качестве последнего шага следует повторить операцию RESTORE с аргументом RECOVERY.  
  
 В аргументе MOVE используется логическое имя файла данных. Чтобы определить логическое имя, выполните следующую инструкцию: `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`  
  
 Следующие примеры включают аргумент FILE, что позволяет указать позицию файла журнала, который требуется восстановить. Чтобы определить позицию файла, выполните следующую инструкцию: `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`  
  
 При восстановлении из копии файлов базы данных и журнала каждую операцию RESTORE следует выполнять отдельно.  
  
```  
-- Restore the report server database and move to new instance folder   
RESTORE DATABASE ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore the report server log file to new instance folder   
RESTORE LOG ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore and move the report server temporary database  
RESTORE DATABASE ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Restore the temporary database log file to new instance folder   
RESTORE LOG ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServer  
   WITH RECOVERY  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServerTempDB  
   WITH RECOVERY  
GO  
```  
  
### <a name="how-to-configure-the-report-server-database-connection"></a>Настройка подключения к базе данных сервера отчетов  
  
1.  Запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и подключитесь к серверу отчетов.  
  
2.  На странице «База данных» нажмите кнопку **Изменить базу данных**. Нажмите кнопку **Далее**.  
  
3.  Щелкните **Выбрать существующую базу данных сервера отчетов**. Нажмите кнопку **Далее**.  
  
4.  Выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором находится база данных сервера отчетов, и нажмите кнопку **Проверить соединение**. Нажмите кнопку **Далее**.  
  
5.  В поле «Имя базы данных» выберите нужную базу данных сервера отчета. Нажмите кнопку **Далее**.  
  
6.  В поле «Учетные данные» укажите учетные данные, которые сервер отчетов будет использовать для подключения к базе данных сервера отчетов. Нажмите кнопку **Далее**.  
  
7.  Нажмите кнопку **Далее** , затем — кнопку **Готово**.  
  
> [!NOTE]  
>  Установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] требует, чтобы экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] включал роль **RSExecRole** . Создание роли, регистрация имени входа и назначения ролей происходят, когда с помощью программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливается подключение к базе данных сервера отчетов. При иных подходах к настройке соединения (особенно если используется программа командной строки rsconfig.exe) сервер отчетов окажется в неработоспособном состоянии. Чтобы сервер отчетов стал доступным, возможно, придется записать код инструментария WMI. Дополнительные сведения см. в разделе [Доступ к поставщику WMI для служб Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  

## <a name="next-steps"></a>Следующие шаги

[Создание RSExecRole](../../reporting-services/security/create-the-rsexecrole.md)   
[Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)   
[Настройка подключения к базе данных сервера отчетов](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
[Настройка учетной записи автоматического выполнения](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
[Диспетчер конфигурации служб Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
[Программа rsconfig](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
[Настройка ключей шифрования и управление ими](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)   
[База данных сервера отчетов](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
