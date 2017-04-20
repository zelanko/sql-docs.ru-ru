---
title: "Заметки о выпуске SQL Server vNext | Документация Майкрософт"
ms.custom: 
ms.date: 03/12/2017
ms.prod: sql-vnext
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
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 93d6640c3842f36f1da10b035ae32b1f0dfc027b
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-vnext-release-notes"></a>Заметки о выпуске SQL Server vNext
В этом разделе описываются ограничения и проблемы, связанные с [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

- Сведения о новых возможностях в этом выпуске см. в разделе [Новые возможности в SQL Server vNext](../sql-server/what-s-new-in-sql-server-vnext.md).
- [Заметки о выпуске SQL Server на платформе Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes) публикуются в нашей новой и развивающейся платформе документации.
- [Заметки о выпуске служб SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md) публикуются в разделе, посвященном службам Reporting Services.

 **Попробуйте продукт:**    
   -   [![Скачать на странице центра оценки](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Скачайте [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на странице **[центра оценки](http://go.microsoft.com/fwlink/?LinkID=829477)**


## <a name="sql-server-vnext-ctp-14-march--2017"></a>SQL Server vNext CTP 1.4 (март 2017 г.)
### <a name="supported-installation-scenarios-ctp-14"></a>Поддерживаемые сценарии установки (CTP 1.4)

### <a name="documentation-ctp-14"></a>Документация (CTP 1.4)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-13-february--2017"></a>SQL Server vNext CTP 1.3 (февраль 2017 г.)
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

## <a name="sql-server-vnext-ctp-12-january--2017"></a>SQL Server vNext CTP 1.2 (январь 2017 г.)
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

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-11-december--2016"></a>SQL Server vNextCTP 1.1 (декабрь 2016 г.)
### <a name="supported-installation-scenarios-ctp-11"></a>Поддерживаемые сценарии установки (CTP 1.1)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] предназначен для использования только в качестве тестовой версии.  Развертывания в рабочей среде не поддерживаются. Рекомендуется установить и протестировать [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на виртуальной машине.

В частности, хотя приведенные ниже сценарии могут подойти вам, они не были тщательно протестированы и **не** поддерживаются в [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]:
- Удаление CTP 1.1.
- Параллельная установка с другими версиями SQL Server.
- Обновление с любой предыдущей версии SQL Server
- В состав установки [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] не входят никакие элементы пакета дополнительных компонентов SQL Server.

### <a name="documentation-ctp-11"></a>Документация (CTP 1.1)
- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , отмечено с помощью раздела **Область применения**. 
- **Проблема и последствия для клиентов.** Локальные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="sql-server-master-data-services-ctp-11"></a>Службы SQL Server Master Data Services (CTP 1.1)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Транзакции могут не работать, если в качестве типа журнала транзакций сущностей задан атрибут
**Проблема и последствия для клиентов:** если для типа журнала транзакций сущностей в **задано значение** Атрибут [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (значение по умолчанию — **Член**), следующие сценарии завершаются с ошибкой:

* Транзакции для изменений сущностей не отображаются на веб-сайте.
* Не удается открыть страницу **Транзакции** на веб-сайте и отменить транзакцию.
* Не удается обновить сущность с помощью заметки транзакции на веб-сайте.

**Обходное решение:**решение отсутствует.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>Копирование версии может не работать, если для параметра **Copy only committed version** (Копировать только зафиксированную версию) задано значение false
-  **Проблема и последствия для клиентов:** если для параметра **Copy only committed version** (Копировать только зафиксированную версию) установлено значение **No** (Нет) (значение по умолчанию — **Yes**(Да)), может произойти сбой операции копирования версии. Сообщение об ошибке не выводится.
-  **Обходное решение:**решение отсутствует.

### <a name="sql-server-integration-services-ssis-ctp-11"></a>Службы SQL Server Integration Services (CTP 1.1)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>Удаление каталога SQL Server Integration Services может завершиться ошибкой, когда установлена функция масштабного развертывания SQL Server Integration Services.
**Проблема и последствия для клиентов**: когда на компьютере установлена функция масштабного развертывания SQL Server Integration Services, удаление базы данных каталога SSISDB может завершиться сбоем со следующей ошибкой: "Не удалось удалить имя входа *"имя_входа"* , так как пользователь в настоящий момент подключен к системе".
   
**Обходной путь**:
-   На компьютере с ролью мастера масштабирования выполните команду "services.msc" для открытия окна "Службы". Остановите службу "SQL Server Integration Services Cluster Master".
-   На компьютерах с рабочей ролью масштабного развертывания, которые подключаются к мастеру, выполните команду "services.msc" для открытия окна "Службы". Остановите службу "SQL Server Integration Services Cluster Worker".

Теперь можно удалить базу данных каталога SSISDB.

#### <a name="odbc-components-are-not-supported-in-this-ctp-release"></a>Компоненты ODBC не поддерживаются в этом выпуске CTP.
**Проблема и последствия для клиентов**: диспетчер подключений, источник и назначение ODBC не поддерживаются в этом выпуске CTP.

**Обходное решение:**решение отсутствует.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-vnext-ctp-10-november-2016"></a>SQL Server vNextCTP 1.0 (ноябрь 2016 г.)
### <a name="supported-installation-scenarios-ctp10"></a>Поддерживаемые сценарии установки (CTP 1.0)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] предназначен для использования только в качестве тестовой версии.  Развертывания в рабочей среде не поддерживаются. Рекомендуется установить и протестировать [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] на виртуальной машине.

В частности, хотя приведенные ниже сценарии могут подойти вам, они не были тщательно протестированы и **не** поддерживаются в [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]:
- Удаление CTP 1.0.
- Параллельная установка с другими версиями SQL Server.
- Обновление с любой предыдущей версии SQL Server
- В состав установки [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] не входят никакие элементы пакета дополнительных компонентов SQL Server.

### <a name="documentation-ctp-10"></a>Документация (CTP 1.0)
- **Проблема и последствия для клиентов:** документация для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Содержимое статей, относящееся к [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] , будет уточнено с помощью **области применения**. 
- **Проблема и последствия для клиентов:** автономные материалы для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]отсутствуют.

### <a name="sql-server-database-engine-ctp-10"></a>Ядро СУБД SQL Server (CTP 1.0)
-  **Проблема и последствия для клиентов:** функция `STRING_AGG` в CTP1 возвращает тип LOB в качестве результата (например, `NVARCHAR(MAX)`). В будущем выпуске CTP такое поведение может измениться и `STRING_AGG` может возвращать `NVARCHAR(4000)` , если входные значения не относятся к типу LOB. Может возникнуть ошибка переполнения, если объединенные результаты не помещаются в `NVARCHAR(4000)`.

-  **Проблема и последствия для клиентов:** избегайте использования незарезервированных ключевых слов, например `WITHIN` в качестве псевдонима для выражений `STRING_AGG`. (Например, `SELECT Company.Name, STRING_AGG(Product.Name, ',') AS WITHIN FROM TableA;`.) В следующем выпуске CTP маркер `WITHIN` после вызова `STRING_AGG` может использоваться как часть функции `STRING_AGG`.

-  **Обходной путь:** избегайте использования псевдонима `WITHIN` или добавьте `AS WITHIN` в качестве спецификации псевдонима во избежание конфликтов с будущими изменениями, которые могут быть внесены в функцию `STRING_AGG`.


### <a name="sql-server-integration-services-ctp-10"></a>Службы SQL Server Integration Services (CTP 1.0)
#### <a name="stop-operation-in-ssis-catalog-may-fail"></a>Остановка операции в каталоге SSIS может завершиться со сбоем
**Проблема и последствия для клиентов:** остановка операции в [!INCLUDE[ssIS_md](../includes/ssis-md.md)] с помощью [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)] или хранимой процедуры catalog.stop_operation может привести к сбою со следующей ошибкой: "Произошла ошибка .NET Framework во время выполнения определяемой пользователем подпрограммы или агрегатной функции 'stop_operation_internal'".

-  **Обходной путь:** откройте диспетчер задач Windows. На вкладке **Процессы** найдите процесс с именем **ISServerExec** и нажмите кнопку **Завершить задачу** , чтобы завершить его.

#### <a name="create-dump-of-ssis-pacakge-execution-may-fail"></a>Создание дампа при выполнении пакета SSIS может завершиться ошибкой
**Проблема и последствия для клиентов:** создание дампа для выполнения пакета с помощью хранимой процедуры catalog.create_execution_dump может привести к сбою со следующей ошибкой: "Произошла ошибка .NET Framework во время выполнения определяемой пользователем подпрограммы или агрегатной функции 'create_execution_dump_internal'".

-  **Обходной путь:** откройте диспетчер задач Windows. На вкладке **Процессы** найдите процесс с именем **ISServerExec**, щелкните его правой кнопкой мыши и выберите **Создать файл дампа**.

#### <a name="get-perf-counter-of-ssis-package-execution-may-fail"></a>Создание счетчика производительности при выполнении пакета SSIS может завершиться ошибкой
**Проблема и последствия для клиентов:** запрос счетчиков производительности [!INCLUDE[ssIS_md](../includes/ssis-md.md)] с помощью функции с табличным значением catalog.dm_execution_performance_counters может привести к сбою со следующей ошибкой: "Произошла ошибка .NET Framework во время выполнения определяемой пользователем подпрограммы или агрегатной функции 'get_execution_perf_counters'".

-  **Обходной путь**: используйте системный монитор Windows, чтобы отслеживать значения счетчиков производительности напрямую. Обходное решение для счетчиков производительности, которые предназначены для выполнения конкретного пакета, отсутствует.

#### <a name="deleting-catalog-may-fail-when-ssis-scale-out-master-is-installed"></a>Удаление каталога может завершиться ошибкой, когда установлена главная роль масштабного развертывания SSIS
**Проблема и последствия для клиентов:** когда на компьютере установлена функция масштабного развертывания [!INCLUDE[ssIS_md](../includes/ssis-md.md)] , удаление каталога **SSISDB** может завершиться сбоем со следующей ошибкой: "Не удалось удалить имя входа ‘…’, , так как пользователь в настоящий момент подключен к системе". 

**Обходной путь**: 
* на компьютере с главной ролью масштабного развертывания выполните команду services.msc для открытия окна **Службы** и остановите службу **SQL Server Integration Services Cluster Master** . 

* На компьютерах с рабочей ролью масштабного развертывания, которые подключаются к главной роли, выполните команду services.msc для открытия окна **Службы** . Остановите службу **SQL Server Integration Services Cluster Worker** . 

Теперь можно удалить каталог **SSISDB** .

#### <a name="odbc-connector-in-ssis-is-not-supported"></a>Соединитель ODBC в SSIS не поддерживается
-  **Проблема и последствия для клиентов:** соединитель ODCB в [!INCLUDE[ssIS_md](../includes/ssis-md.md)] не поддерживается.
-  **Обходное решение:** решение отсутствует.

### <a name="sql-server-reporting-services-ctp-10"></a>Службы SQL Server Reporting Services (CTP 1.0)

Службы SQL Server Reporting Services не содержат новых возможностей для [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-master-data-services-ctp-10"></a>Службы SQL Server Master Data Services (CTP 1.0)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Транзакции могут не работать, если в качестве типа журнала транзакций сущностей задан атрибут
**Проблема и последствия для клиентов:** если для типа журнала транзакций сущностей в **задано значение** Атрибут [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (значение по умолчанию — **Член**), следующие сценарии завершаются с ошибкой:

* Транзакции для изменений сущностей не отображаются на веб-сайте.
* Не удается открыть страницу **Транзакции** на веб-сайте и отменить транзакцию.
* Не удается обновить сущность с помощью заметки транзакции на веб-сайте.

**Обходное решение:**решение отсутствует.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>Копирование версии может не работать, если для параметра **Copy only committed version** (Копировать только зафиксированную версию) задано значение false
**Проблема и последствия для клиентов:** если для параметра **Copy only committed version** (Копировать только зафиксированную версию) установлено значение **No** (Нет) (значение по умолчанию — **Yes**(Да)), может произойти сбой операции копирования версии. Сообщение об ошибке не выводится.

**Обходное решение:**решение отсутствует.
 
### <a name="sql-server-management-studio-ssms-ctp-10"></a>SQL Server Management Studio (SSMS) (CTP 1.0)
SQL Server Management Studio скачивается отдельно.  Актуальные сведения см. в [заметках о выпуске SQL Server Management Studio](https://msdn.microsoft.com/library/mt238486.aspx).

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Общение с командой разработчиков SQL Server 
- [Stack Overflow (тег sql сервера) — задавайте технические вопросы](http://stackoverflow.com/questions/tagged/sql-server)
- [Форумы MSDN — задавайте технические вопросы](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect — сообщайте об ошибках и запрашивайте функции](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit — общее обсуждение по поводу R](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


