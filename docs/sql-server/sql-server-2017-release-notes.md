---
title: "Заметки о выпуске SQL Server 2017 | Документация Майкрософт"
ms.custom: 
ms.date: 05/16/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: a2950b6aef0e12653efbb9eb26fd3f1ae6cb951e
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="sql-server-2017-release-notes"></a>Заметки о выпуске SQL Server 2017
В этом разделе описываются ограничения и проблемы, связанные с [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Дополнительные сведения см. в следующих разделах:

- [Новые возможности в SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).
- [Заметки о выпуске SQL Server на платформе Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
- [Заметки о выпуске служб SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).

 **Попробуйте продукт:**    
   -   [![Скачать на странице центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Скачайте [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на странице **[центра оценки](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>Релиз-кандидат SQL Server 2017 (RC1 — июль 2017 г.)

### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 — июль 2017 г.)
- **Проблема и ее эффект для клиента**: параметр *runincluster* хранимой процедуры **[catalog].[create_execution]** переименован в *runinscaleout* для согласованности и удобства чтения.
- **Обходной путь**: если у вас есть сценарии для запуска пакетов в Scale Out, нужно изменить имя параметра с *runincluster* на *runinscaleout*, чтобы они работали в RC1.

- **Проблема и ее эффект для клиента**: SQL Server Management Studio (SSMS) 17.1 и более ранние версии не могут активировать выполнение пакета в Scale Out в RC1. Сообщение об ошибке: "*@runincluster* не является параметром процедуры **create_execution**". Эта проблема будет исправлена в следующем выпуске SSMS, в версии 17.2. Версии SSMS, начиная с 17.2, поддерживают новое имя параметра и выполнение пакетов в Scale Out. 
- **Обходной путь**: пока не станет доступна версия SSMS 17.2, вы можете создать сценарий выполнения пакетов в имеющейся у вас версии SSMS, а затем изменить в нем имя параметра *runincluster* на *runinscaleout* и запустить сценарий.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server 2017 CTP 2.1 (май 2017 г.)
### <a name="documentation-ctp-21"></a>Документация (CTP 2.1)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="sql-server-reporting-services-ctp-21"></a>Службы SQL Server Reporting Services (CTP 2.1)

- **Проблема и последствия для клиентов.** Если серверы отчетов SQL Server Reporting Services и Power BI установлены на одном и том компьютере и один из них будет удален, вы больше не сможете подключиться к оставшемуся серверу отчетов через диспетчер конфигурации сервера отчетов.
- **Обходной путь.** Чтобы обойти эту проблему, после удаления одного из этих серверов выполните указанные ниже операции.

    1. Запустите командную строку с правами администратора.
    2. Откройте каталог, в который установлен оставшийся сервер отчетов.

        *Сервер отчетов Power BI по умолчанию размещается в папке C:\Program Files\Microsoft Power BI Report Server*.

        *Сервер отчетов SQL Server Reporting Services по умолчанию размещается в папке: C:\Program Files\Microsoft SQL Server Reporting Services*.

    3. Затем откройте следующую папку. В зависимости от того, какой сервер отчетов у вас остался, это будет папка *SSRS* или *PBIRS*.
    4. Перейдите в папку WMI.
    5. Выполните следующую команду:

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        Если появится указанное ниже сообщение об ошибке, его можно игнорировать.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **Проблема и последствия для клиентов.** После установки на компьютер с установленной версией *TSqlLanguageService.msi* 2016 (с помощью программы установки SQL или из отдельного дистрибутива) с него удаляются сборки *Microsoft.SqlServer.Management.SqlParser.dll* и *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* версии 13.* (SQL 2016). В результате все приложения, которые имеют зависимость от версии 2016 этих сборок, прекращает функционировать и выдают сообщение об ошибке следующего вида: *ошибка: не удалось загрузить файл или сборку 'Microsoft.SqlServer.Management.SqlParser, Version=13.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' либо одну из ее зависимостей. Системе не удается найти указанный файл.*

   При этом попытки переустановить версию TSqlLanguageService.msi 2016 завершаются сбоем и выдается следующее сообщение: *Служба языка T-SQL Microsoft SQL Server 2016 не установлена, так как на компьютере уже имеется более поздняя версия*.

- **Обходной путь.** Чтобы обойти эту проблему и устранить неполадки с приложением, которое зависит от версии 13 указанных сборок, выполните следующие действия:

   1. Откройте раздел **Установка и удаление программ**.
   1. Найдите *службу языка T-SQL Microsoft SQL Server vNext CTP2.1*, щелкните ее правой кнопкой мыши и выберите команду **Удалить**.
   1. Когда компонент будет удален, восстановите неисправное приложение (или переустановите соответствующую версию *TSqlLanguageService.MSI*).

   В результате выполнения этих действий версия 14 указанных сборок будет удалена, так что все приложения, которые зависят от версии 14, перестанут функционировать. Если вам требуются эти сборки, необходимо установить их отдельно, а не параллельно с установками версии 2016.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (апрель 2017 г.)
### <a name="documentation-ctp-20"></a>Документация (CTP 2.0)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="always-on-availability-groups"></a>Группы доступности AlwaysOn

- **Проблема и последствия для клиентов.** Экземпляр SQL Server, в котором размещается вторичная реплика группы доступности, завершается сбоем, если основная версия SQL Server ниже версии экземпляра, в котором находится первичная реплика. Это касается обновлений из всех поддерживаемых версий SQL Server, в которых хранятся группы доступности, на SQL Server [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 2.0. Проблема возникает при выполнении следующих действий: 

> 1. Пользователь обновляет экземпляр SQL Server, в котором находится вторичная реплика, в соответствии с [рекомендациями](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).
> 2. После обновления происходит сбой и до тех пор, пока не будут обновлены все вторичные реплики в группе доступности, обновленная вторичная реплика становится первичной. При этом прежняя основная реплика становится первичной репликой, версия которой ниже, чем версия первичной реплики.
> 3. Группа доступности получает неподдерживаемую конфигурацию, а все оставшиеся вторичные реплики становятся подверженными сбоям. 

- **Обходной путь.** Подключитесь к экземпляру SQL Server, на котором находится новая первичная реплика, и удалите неисправную вторичную реплику из конфигурации.

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   Это восстановит экземпляр SQL Server, в котором находится вторичная реплика.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql сервера) — задавайте технические вопросы](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN — задавайте технические вопросы](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по поводу R](https://www.reddit.com/r/SQLServer/)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
