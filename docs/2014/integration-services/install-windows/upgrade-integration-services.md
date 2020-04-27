---
title: Обновление служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, upgrading
- SSIS, upgrading
- SQL Server Integration Services, upgrading
- upgrading Integration Services
ms.assetid: 04f9863c-ba0b-47c5-af91-f2d41b078a23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d1e40954a5a5eb7a69ba4f70b798356f38175fed
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62768094"
---
# <a name="upgrade-integration-services"></a>Обновление служб Integration Services
  Если на компьютере установлены службы [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], их вы можете обновить до [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
 При обновлении до [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] на компьютере, где установлена одна из предыдущих версий [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] устанавливается параллельно с более ранней версией.  
  
 Вместе с этой параллельной установкой устанавливается несколько версий программы dtexec. Чтобы убедиться в том, что запускается правильная версия программы, в командной строке запустите программу, введя полный путь (\<диск>:\Program Files\Microsoft SQL Server\\<версия\>\DTS\Binn). Дополнительные сведения о программе dtexec см. в разделе [dtexec Utility](../packages/dtexec-utility.md).  
  
> [!NOTE]  
>  В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все пользователи в группе пользователей имели доступ к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . При установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]пользователи не имеют доступа к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . По умолчанию эта служба является защищенной. После установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] администратор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен запустить средство настройки DCOM (Dcomcnfg.exe), чтобы предоставить конкретным пользователям доступ к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Дополнительные сведения см. в статье [Grant Permissions to Integration Services Service](../grant-permissions-to-integration-services-service.md).  
  
## <a name="before-upgrading-integration-services"></a>До обновления служб Integration Services  
 Рекомендуется перед обновлением до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]запустить помощник по обновлению. Помощник по обновлению сообщит о проблемах, которые могут возникнуть при обновлении существующих пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] до нового формата [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
> [!NOTE]
>  В текущем выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]поддержка миграции или выполнения пакетов служб DTS прекращена. Следующие функциональные возможности служб DTS более не поддерживаются.  
> 
>  -   Среда выполнения DTS  
> -   API-интерфейс служб DTS  
> -   Мастер миграции пакетов служб DTS, выполняющий перенос пакетов DTS в следующую версию служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
> -   Поддержка обслуживания пакета служб DTS в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
> -   Задача «Выполнение пакета служб DTS 2000»  
> -   Сканирование пакетов DTS, выполняемое помощником по обновлению.  
> 
>  Дополнительные сведения о других неподдерживаемых функциях см. [в разделе неподдерживаемые функции Integration Services в SQL Server 2014](../discontinued-integration-services-functionality-in-sql-server-2014.md).  
  
## <a name="upgrading-integration-services"></a>обновление служб Integration Services  
 Обновление можно выполнить одним из следующих способов.  
  
-   Запустите [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] программу установки и выберите вариант **обновления с SQL Server 2005, SQL Server 2008 или SQL Server 2008 R2**или **[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]**.  
  
-   Запустите **файл Setup. exe** из командной строки и укажите `/ACTION=upgrade` параметр. Дополнительные сведения см. в подразделе «сценарии установки для [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]» раздела [Install SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 Обновление не следует применять для выполнения следующих действий.  
  
-   Изменение конфигурации существующей установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Переход с 32-разрядной на 64-разрядную или 64-разрядной на 32-разрядную версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Переход на другую локализованную версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Можно обновить службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вместе с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], только компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]либо только службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если обновить только компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], службы [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] останутся в рабочем состоянии, но функциональность [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] будет отсутствовать. Если обновить только службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], то службы [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] будут обладать полной функциональностью, но смогут хранить пакеты только в файловой системе, если экземпляр компонента [!INCLUDE[ssDECurrent](../../includes/ssdecurrent-md.md)] не будет доступен на другом компьютере.  
  
## <a name="upgrading-both-integration-services-and-the-database-engine-to-sscurrent"></a>Обновление служб Integration Services вместе с компонентом ядра СУБД до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 В этом разделе описаны последствия, к которым может привести обновление со следующими критериями.  
  
-   Обновление служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]производится одновременно.  
  
-   И службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , и экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] находятся на одном компьютере.  
  
### <a name="what-the-upgrade-process-does"></a>Действия, выполняемые при обновлении  
 Процесс обновления заключается в выполнении следующих задач.  
  
-   Устанавливает файлы, службы и средства [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] (в средах[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]). Если есть несколько экземпляров [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] на одном компьютере, при первом обновлении какого-либо экземпляра до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] устанавливаются файлы, службы и средства [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   Обновляет экземпляр [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии.  
  
-   Перемещает данные из [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] системных [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] таблиц или в [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] системные таблицы следующим образом:  
  
    -   Перенос пакетов без изменений из системной таблицы msdb.dbo.sysdtspackages90 в системную таблицу msdb.dbo.sysssispackages.  
  
        > [!NOTE]  
        >  Несмотря на то, что данные переносятся в другую системную таблицу, процесс обновления не производит перенос пакетов в другой формат.  
  
    -   Перенос метаданных папок из системной таблицы msdb.sysdtsfolders90 в системную таблицу msdb.sysssisfolders.  
  
    -   Перенос данных журналов из системной таблицы msdb.sysdtslog90 в системную таблицу msdb.sysssislog.  
  
-   Удаление системных таблиц msdb.sysdts*90 и хранимых процедур для доступа к ним после переноса данных в новые таблицы msdb.sysssis\* . Однако при обновлении таблица sysdtslog90 заменяется представлением, которое также носит имя sysdtslog90. Новое представление sysdtslog90 отображает новую системную таблицу msdb.sysssislog. Это гарантирует, что все отчеты, основанные на таблице журнала, будут выполняться без проблем.  
  
-   Создаются три новые предопределенные роли базы данных, db_ssisadmin, db_ssisltduser и db_ssisoperator, предназначенные для управления доступом к пакетам. Роли [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — db_dtsadmin, db_dtsltduser и db_dtsoperator — не удаляются, но становятся членами соответствующих новых ролей.  
  
-   Если хранилище [!INCLUDE[ssIS](../../includes/ssis-md.md)] пакетов (то есть расположение файловой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] системы, управляемое службой) является расположением по умолчанию в папке **\SQL Server\90**, **\SQL Server\100**или **\SQL Server\110** , эти пакеты перемещаются в новое расположение по умолчанию в **\SQL Server\120**.  
  
-   Изменение файла конфигурации служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , чтобы он указывал на обновленный экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
### <a name="what-the-upgrade-process-does-not-do"></a>Действия, не выполняемые при обновлении  
 Процесс обновления не включает следующие задачи.  
  
-   **Не** Удаляет службу [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] .  
  
-   Не выполняется перенос существующих пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в формат пакетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Сведения о переносе пакетов см. в разделе [Обновление пакетов служб Integration Services](upgrade-integration-services-packages.md).  
  
-   Не производится перенос пакетов, расположенных в файловой системе в месте, отличном от расположения по умолчанию, добавленного в файл конфигурации служб. Если файл конфигурации ранее изменялся, и в него были добавлены папки файловой системы, хранящиеся в этих папках пакеты не будут перенесены в новое местоположение.  
  
-   В шагах задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где выполняется непосредственный вызов служебной программы **dtexec** (dtexec.exe), путь к программе **dtexec** в файловой системе не изменяется. В этих шагах задания нужно вручную изменить путь файловой системы, чтобы задать правильное местонахождение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для служебной программы **dtexec** .  
  
### <a name="what-you-can-do-after-upgrading"></a>Действия после обновления  
 После завершения обновления можно выполнить следующие задачи.  
  
-   Запускать задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые выполняют пакеты.  
  
-   Используется [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для управления [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетами, хранящимися в экземпляре [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Необходимо внести изменения в файл конфигурации службы, добавив экземпляр [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] в список расположений, управляемых службой.  
  
    > [!NOTE]  
    >  С помощью предыдущих версий среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] подключиться к службе [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] нельзя.  
  
-   Выяснить версии пакетов системной таблицы msdb.dbo.sysssispackages можно по значениям столбца packageformat. В этом столбце содержатся номера версий для каждого из пакетов. Значение 2 указывает на пакет служб [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], а значение 3 — на пакет служб [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]. До переноса пакетов в новый формат значение в столбце packageformat не изменится.  
  
-   Для проектирования, запуска [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] управления [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетами нельзя использовать инструменты или. Средства [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] включают в себя соответствующие версии среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], мастер импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также программу выполнения пакетов (dtexecui.exe). В процессе обновления не удаляются средства [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. Однако эти средства нельзя будет использовать для работы с пакетами служб [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] на обновленных серверах.  
  
-   По умолчанию при установке обновления служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] настраивается для регистрации событий, связанных с запуском пакетов, в журнал событий приложений. При использовании компонента сборщика данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]эта настройка может вызвать появление в журнале событий слишком большого числа записей. К числу регистрируемых событий относятся EventID 12288, «Пакет запущен» и EventID 12289, «Выполнение пакета завершилось успешно». Чтобы исключить регистрацию этих двух событий в журнале событий приложений, откройте реестр для изменения. Затем найдите в реестре узел HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS node и измените значение DWORD параметра LogPackageExecutionToEventLog с 1 на 0.  
  
## <a name="upgrading-only-the-database-engine-to-sscurrent"></a>Обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 В этом разделе описаны последствия, к которым может привести обновление со следующими критериями.  
  
-   Обновляется только экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Иначе говоря, экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] обновляется до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], а экземпляр служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и клиентские средства сохраняются в версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
-   Экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] находится на одном компьютере, а службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и клиентские средства — на другом.  
  
### <a name="what-you-can-do-after-upgrading"></a>Действия после обновления  
 Системные таблицы, в которых хранятся пакеты на обновленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], отличаются от системных таблиц, используемых в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. Таким образом, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] не могут обнаруживать пакеты в системных таблицах на обновленном экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Это ограничивает ряд доступных для выполнения задач.  
  
-   Средства [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и среда [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], не могут использоваться на других компьютерах для загрузки пакетов с обновленного экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и управления ими.  
  
    > [!NOTE]  
    >  Хотя перенос пакетов на обновленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в новый формат еще не произведен, их нельзя обнаружить средствами [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]. Поэтому невозможно и их использование средствами [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
-   Нельзя использовать [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] на других компьютерах для выполнения пакетов, хранящихся в базе данных msdb на обновленном экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] не могут использоваться для выполнения пакетов служб [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] или [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], хранящихся на обновленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [Использование существующих пользовательских расширений служб SSIS и приложений в Denali](https://go.microsoft.com/fwlink/?LinkId=238157)на blogs.msdn.com.  
  
  
