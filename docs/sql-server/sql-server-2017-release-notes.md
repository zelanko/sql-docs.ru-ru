---
title: "Заметки о выпуске SQL Server 2017 г. | Документы Microsoft"
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
ms.lasthandoff: 07/17/2017

---
# <a name="sql-server-2017-release-notes"></a>Заметки о выпуске SQL Server 2017 г.
В этом разделе описываются ограничения и проблемы, связанные с [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Другую информацию по этой теме можно найти в следующих разделах:

- [Новые возможности SQL Server 2017 г](../sql-server/what-s-new-in-sql-server-2017.md).
- [SQL Server в заметках о выпуске Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
- [Заметки о выпуске служб SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).

 **Попробуйте продукт:**    
   -   [![Скачать на странице центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Скачайте [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на странице **[центра оценки](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>Релиз-кандидат SQL Server 2017 (RC1 — июль 2017 г.)

### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 — июль 2017 г.)
- **Проблема и ее эффект для клиента**: параметр *runincluster* хранимой процедуры **[catalog].[create_execution]** переименован в *runinscaleout* для согласованности и удобства чтения.
- **Обходной путь**: если у вас есть сценарии для запуска пакетов в Scale Out, нужно изменить имя параметра с *runincluster* на *runinscaleout*, чтобы они работали в RC1.

- **Проблема и ее эффект для клиента**: SQL Server Management Studio (SSMS) 17.1 и более ранние версии не могут активировать выполнение пакета в Scale Out в RC1. Сообщение об ошибке: "*@runincluster* не является параметром процедуры **create_execution**". Эта проблема будет исправлена в следующем выпуске SSMS, в версии 17.2. Версии SSMS, начиная с 17.2, поддерживают новое имя параметра и выполнение пакетов в Scale Out. 
- **Обходной путь**: пока не станет доступна версия SSMS 17.2, вы можете создать сценарий выполнения пакетов в имеющейся у вас версии SSMS, а затем изменить в нем имя параметра *runincluster* на *runinscaleout* и запустить сценарий.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-21-may--2017"></a>2017 г. SQL Server CTP 2.1 (май 2017 г.)
### <a name="documentation-ctp-21"></a>Документация (CTP-версия 2.1)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP-версия 2.1)

- **Проблема и последствия для клиентов:** при наличии служб SQL Server Reporting Services и Power BI сервера отчетов на том же компьютере и удалить один из них, больше не можно соединиться с сервером отчетов в оставшихся с диспетчером конфигурации сервера отчетов.
- **Инструкции по решению** Чтобы обойти эту проблему, необходимо выполнить следующие операции после удаления одного из серверов.

    1. Откройте командную строку с правами администратора.
    2. Перейдите в каталог, где оставшиеся сервер отчетов установлен.

        *Расположение по умолчанию для сервера отчетов Power BI: C:\Program Files\Microsoft Power BI отчета сервера*

        *Расположение по умолчанию для SQL Server Reporting Services: C:\Program Files\Microsoft SQL Server Reporting Services*

    3. Затем перейдите к следующей папке. Это будет *SSRS* или *PBIRS* в зависимости от того, что остается.
    4. Перейдите в папку WMI.
    5. Выполните следующую команду:

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        Если вы видите его следующей ошибки можно игнорировать.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP-версия 2.1)

- **Проблема и последствия для клиентов:** после установки на компьютере с версии 2016 *TSqlLanguageService.msi* (либо через программу установки SQL или установлены как автономный распространяемый пакет) версии v13.* (SQL 2016) *Microsoft.SqlServer.Management.SqlParser.dll* и *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* удаляются. Все приложения, которые имеют зависимость от версии 2016 этих сборок затем прекращает работать, предоставляя сообщение об ошибке: *ошибка: не удалось загрузить файл или сборку ' Microsoft.SqlServer.Management.SqlParser, версия = 13.0.0.0, язык и региональные параметры = neutral, PublicKeyToken = 89845dcd8080cc91 "или одну из ее зависимостей. Системе не удается найти указанный файл.*

   Кроме того, попытки переустановите версию 2016 TSqlLanguageService.msi завершится ошибкой с сообщением: *не удалось выполнить установку из служба Microsoft SQL Server 2016 T-SQL языка, поскольку более поздняя версия уже существует на компьютере*.

- **Инструкции по решению** решить эту проблему и исправить приложение, которое зависит от v13 версии сборок, выполните следующие действия:

   1. Последовательно выберите пункты **Установка и удаление программ**
   1. Найти *Microsoft SQL Server vNext CTP2.1 служба языка T-SQL*, щелкните его правой кнопкой мыши и выберите **удаления**.
   1. После удаления компонента Восстановление приложения, который прерывается (или повторно установить соответствующую версию *TSqlLanguageService.MSI*)

   Этот обходной путь приведет к удалению v14 версии сборок, поэтому все приложения, которые зависят от версий v14 больше не будет работать. Если требуются эти сборки, без любой 2016 устанавливает side-by-side отдельная установка не требуется.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>2017 г. SQL Server CTP 2.0 (апрель 2017 г.)
### <a name="documentation-ctp-20"></a>Документация (CTP 2.0)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="always-on-availability-groups"></a>Группы доступности AlwaysOn

- **Проблема и последствия для клиентов:** размещение вторичной реплики группы доступности экземпляр SQL Server аварийно завершает работу, если основной номер версии SQL Server меньше экземпляр, на котором размещена первичная реплика. Влияет на обновления из всех поддерживаемых версиях SQL Server, содержащие группы доступности в SQL Server [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 2.0. Это происходит в списке следующие действия. 

> 1. Пользователь производит обновление SQL Server экземпляра размещения вторичной реплики в соответствии с [рекомендации](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).
> 2. После обновления отработки отказа и только что обновленную вторичную станет основной перед завершением обновления для всех вторичных реплик в группе доступности. Старая первичная сейчас получателя, который является более ранняя версия, чем основной.
> 3. Группа доступности находится в неподдерживаемой конфигурацией и всех оставшихся вторичных репликах могут оказаться уязвимыми к сбою. 

- **Инструкции по решению** подключение к экземпляру SQL Server, в котором новая первичная реплика и удалите неисправный вторичной реплики из конфигурации.

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   Восстанавливает экземпляр SQL Server, на котором размещается вторичная реплика.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql сервера) — задавайте технические вопросы](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN — задавайте технические вопросы](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по поводу R](https://www.reddit.com/r/SQLServer/)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
