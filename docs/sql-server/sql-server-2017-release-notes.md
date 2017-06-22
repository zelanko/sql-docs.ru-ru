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
ms.translationtype: Human Translation
ms.sourcegitcommit: 67c1c0f3a9da6cc5d050da5db8a493f5da934c2a
ms.openlocfilehash: fa45fea4ebb378f035b4b4af2b1fa8a20bc152a5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-2017-release-notes"></a>Заметки о выпуске SQL Server 2017 г.
В этом разделе описываются ограничения и проблемы, связанные с [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Связанные сведения содержатся в следующих разделах:

- [Новые возможности SQL Server 2017 г](../sql-server/what-s-new-in-sql-server-2017.md).
- [SQL Server в заметках о выпуске Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
- [Заметки о выпуске SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).

 **Попробуйте продукт:**    
   -   [![Скачать на странице центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Скачайте [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на странице **[центра оценки](http://go.microsoft.com/fwlink/?LinkID=829477)**

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


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-14-march--2017"></a>SQL Server CTP 2017 г. 1.4 (март 2017 г.)

### <a name="documentation-ctp-14"></a>Документация (CTP 1.4)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-13-february--2017"></a>SQL Server CTP 2017 г. 1.3 (февраля 2017 г.)
### <a name="supported-installation-scenarios-ctp-13"></a>Поддерживаемые сценарии установки (CTP 1.3)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] предназначен для использования только в качестве тестовой версии.  Развертывания в рабочей среде не поддерживаются. Рекомендуется установить и протестировать [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на виртуальной машине.

### <a name="documentation-ctp-13"></a>Документация (CTP 1.3)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="sql-server-integration-services-ssis-ctp-13"></a>Службы SQL Server Integration Services (SSIS) (CTP 1.3)
#### <a name="cdc-components-not-supported-in-this-ctp-release"></a>Компоненты CDC не поддерживаются в этом выпуске CTP
-   **Проблема и последствия для клиентов.**Задача управления CDC, CDC-источник и разделитель CDC не поддерживаются в этом выпуске CTP.
-   **Обходное решение:**решение отсутствует.


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-12-january--2017"></a>SQL Server CTP 2017 г 1.2 (января 2017 г.)
### <a name="supported-installation-scenarios-ctp-12"></a>Поддерживаемые сценарии установки (CTP 1.2)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] предназначен для использования только в качестве тестовой версии.  Развертывания в рабочей среде не поддерживаются. Рекомендуется установить и протестировать [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на виртуальной машине.

### <a name="sql-server-database-engine-ctp-12"></a>Ядро СУБД SQL Server (CTP 1.2)
- **Проблема и последствия для клиентов.** В некоторых случаях служба MSSQLSERVER может переставать отвечать на запросы в состоянии запуска.
- **Обходное решение.** Для устранения этой проблемы сделайте следующее:
  -  Создайте зависимость между службами `mssqlserver` и `keyiso` . Один из способов сделать это — выполнить следующую команду из командной строки с повышенными привилегиями: `sc config mssqlserver depend= keyiso`
  - Перезагрузите компьютер.

### <a name="documentation-ctp-12"></a>Документация (CTP 1.2)
- **Проблема и последствия для клиентов:** документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.
 
### <a name="sql-server-integration-services-ssis-ctp-12"></a>Службы SQL Server Integration Services (SSIS) (CTP 1.2)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>Удаление каталога SQL Server Integration Services может завершиться ошибкой, когда установлена функция масштабного развертывания SQL Server Integration Services.
**Проблема и последствия для клиентов**: когда на компьютере установлена функция масштабного развертывания SQL Server Integration Services, удаление базы данных каталога SSISDB может завершиться сбоем со следующей ошибкой: "Не удалось удалить имя входа *"имя_входа"* , так как пользователь в настоящий момент подключен к системе".
   
**Обходной путь**:
-   На компьютере с ролью мастера масштабирования выполните команду "services.msc" для открытия окна "Службы". Остановите службу "SQL Server Integration Services Cluster Master".
-   На компьютерах с рабочей ролью масштабного развертывания, которые подключаются к мастеру, выполните команду "services.msc" для открытия окна "Службы". Остановите службу "SQL Server Integration Services Cluster Worker".

Теперь можно удалить базу данных каталога SSISDB.

### <a name="sql-server-master-data-services-ctp-12"></a>Службы SQL Server Master Data Services (CTP 1.2)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Транзакции могут не работать, если в качестве типа журнала транзакций сущностей задан атрибут
**Проблема и последствия для клиентов:** если для типа журнала транзакций сущностей в **задано значение** Атрибут [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (значение по умолчанию — **Член**), следующие сценарии завершаются с ошибкой:

* Транзакции для изменений сущностей не отображаются на веб-сайте.
* Не удается открыть страницу **Транзакции** на веб-сайте и отменить транзакцию.
* Не удается обновить сущность с помощью заметки транзакции на веб-сайте.

**Обходное решение:**решение отсутствует.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>Копирование версии может не работать, если для параметра **Copy only committed version** (Копировать только зафиксированную версию) задано значение false
-  **Проблема и последствия для клиентов:** если для параметра **Copy only committed version** (Копировать только зафиксированную версию) установлено значение **No** (Нет) (значение по умолчанию — **Yes**(Да)), может произойти сбой операции копирования версии. Сообщение об ошибке не выводится.
-  **Обходное решение:**решение отсутствует.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql сервера) — задавайте технические вопросы](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN — задавайте технические вопросы](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по поводу R](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


