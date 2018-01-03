---
title: "Новые возможности служб Integration Services в SQL Server 2017 | Документы Майкрософт"
ms.custom: 
ms.date: 09/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7e7b7e796c6badea38ea4423561d26e7f53eb95d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="what39s-new-in-integration-services-in-sql-server-2017"></a>Новые возможности служб Integration Services в SQL Server 2017
В этой статье описаны функции, которые были добавлены или обновлены в [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE]
> В SQL Server 2017 также входят функции SQL Server 2016 и функции, добавленные в обновлениях для SQL Server 2016. Сведения о новых возможностях служб SQL Server Integration Services в SQL Server 2016 см. в разделе [Новые возможности служб Integration Services в SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="highlights-of-this-release"></a>Главное в этом выпуске

Ниже представлены самые важные возможности служб Integration Services в SQL Server 2017.

-   **Scale Out**. Легко распределяйте выполнение пакетов SSIS между несколькими компьютерами с рабочей ролью и управляйте выполнениями и рабочими ролями с одного главного компьютера. Дополнительные сведения см. в разделе [Масштабное развертывание служб Integration Services](../integration-services/scale-out/integration-services-ssis-scale-out.md).

-   **Службы Integration Services в Linux**. Выполняйте пакеты SSIS на компьютерах с ОС Linux. Дополнительные сведения см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

-   **Улучшенные возможности подключения**. Подключайтесь к веб-каналам OData в Microsoft Dynamics AX Online и Microsoft Dynamics CRM Online с помощью обновленных компонентов OData. 

## <a name="new-in-azure-data-factory"></a>Новые возможности фабрики данных Azure

В общедоступной предварительной версии 2 фабрики данных Azure, выпущенной в сентябре 2017 г., теперь можно выполнять следующие действия:
-   развертывать пакеты в базе данных каталога служб SSIS (SSISDB) в базе данных SQL Azure;
-   запускать пакеты, развернутые в Azure, в Azure-SSIS Integration Runtime, компоненте фабрики данных Azure версии 2.

Дополнительные сведения см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Для этих новых возможностей требуются средства SQL Server Data Tools (SSDT) версии 17.2 или более поздней, но не требуется SQL Server 2017 или SQL Server 2016. При развертывании пакетов в Azure мастер развертывания пакетов всегда обновляет их до новейшего формата.

## <a name="new-in-the-azure-feature-pack"></a>Новые возможности в пакете дополнительных компонентов Azure

Помимо улучшенных возможностей подключения в SQL Server, в пакете дополнительных компонентов служб Integration Services для Azure добавлена поддержка Azure Data Lake Store. Дополнительные сведения см. в записи блога [New Azure Feature Pack Release Strengthening ADLS Connectivity](https://blogs.msdn.microsoft.com/ssis/2017/08/29/new-azure-feature-pack-release-strengthening-adls-connectivity/) (Новый пакет дополнительных компонентов для Azure улучшает подключение к ADLS). Также см. раздел [Пакет дополнительных компонентов Azure для служб Integration Services (SSIS)](azure-feature-pack-for-integration-services-ssis.md).

## <a name="new-in-sql-server-data-tools-ssdt"></a>Новые возможности в SQL Server Data Tools (SSDT)

Теперь в Visual Studio 2017 или Visual Studio 2015 можно разрабатывать проекты и пакеты SSIS, предназначенные для SQL Server версий 2012–2017. Дополнительные сведения см. в разделе [Скачивание SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="new-in-ssis-in-sql-server-2017-rc1"></a>Новые возможности служб SSIS в версии-кандидате 1 SQL Server 2017

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Новые и измененные функции в Scale Out для служб SSIS

-   Мастер масштабирования Scale Out теперь поддерживает высокий уровень доступности. Вы можете включить AlwaysOn для базы данных SSISDB и настроить отказоустойчивую кластеризацию Windows Server для сервера, на котором размещается главная служба Scale Out. Применение этого изменения к главной службе Scale Out позволяет избежать единой точки отказа и обеспечить высокую доступность всего развертывания Scale Out.
-   Улучшена отработка отказа для журналов выполнения из рабочих ролей масштабирования Scale Out. Журналы выполнения сохраняются на локальном диске, если рабочая роль Scale Out неожиданно прекращает работу. После перезапуска рабочей роли сохраняемые журналы загружаются повторно и продолжают сохраняться в базе данных SSISDB.
-   Параметр *runincluster* хранимой процедуры **[catalog].[create_execution]** переименован в *runinscaleout* для согласованности и удобства чтения. Это изменение имеет указанные ниже последствия.
    -   Если у вас есть скрипты для запуска пакетов в Scale Out, нужно изменить имя параметра с *runincluster* на *runinscaleout*, чтобы они работали в RC1.
    -   SQL Server Management Studio (SSMS) 17.1 и более ранние версии не могут активировать выполнение пакета в Scale Out в RC1. Сообщение об ошибке: "*@runincluster* не является параметром процедуры **create_execution**". Эта проблема будет исправлена в следующем выпуске SSMS, в версии 17.2. Версии SSMS начиная с 17.2 поддерживают новое имя параметра и выполнение пакетов в Scale Out. Пока не станет доступна версия SSMS 17.2, в качестве обходного решения вы можете создать скрипт выполнения пакетов в имеющейся у вас версии SSMS, а затем изменить в нем имя параметра *runincluster* на *runinscaleout* и запустить скрипт.
-   Каталог SSIS содержит новое глобальное свойство, позволяющее указать режим по умолчанию для выполнения SSIS-пакетов. Это новое свойство применяется при вызове хранимой процедуры **[catalog].[create_execution]** с параметром *runinscaleout*, имеющим значение NULL. Этот режим также применяется к заданиям агента SQL служб SSIS. Новое глобальное свойство можно задать в диалоговом окне "Свойства" для узла SSISDB в SQL Server Management Studio или с помощью следующей команды:
    ```sql
    EXEC [catalog].[configure_catalog] @property_name=N'DEFAULT_EXECUTION_MODE', @property_value=1
    ```

## <a name="new-in-ssis-in-sql-server-2017-ctp-21"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 2.1

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Новые и измененные функции в Scale Out для служб SSIS

-   Теперь вы можете использовать параметр **Use32BitRuntime** при активации выполнения в Scale Out.
-   Повышена производительность записи данных журналов, связанных с выполнением пакетов в Scale Out, в базу данных SSISDB. Журналы сообщений о событиях и контексте сообщений теперь записываются в базу данных SSISDB в пакетном режиме, а не по отдельности. Примечания касательно этого улучшения:        
    - В некоторых отчетах в текущей версии SQL Server Management Studio (SSMS) эти журналы, связанные с выполнениями в Scale Out, в настоящее время не приводятся. Предполагается, что они будут поддерживаться в следующем выпуске SSMS. Это касается отчета *Все соединения*, отчета *Контекст ошибки* и раздела *Сведения о подключении* на панели мониторинга службы Integration Service.
    - Добавлен новый столбец **event_message_guid**. Этот столбец можно использовать для объединения представлений [catalog].[event_message_context] и [catalog].[event_messages] вместо использования **event_message_id** при запросе журналов выполнений в Scale Out.
-   Чтобы получить приложение для управления компонентом SSIS Scale Out, [скачайте SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17.1 или более поздней версии.

## <a name="new-in-ssis-in-sql-server-2017-ctp-20"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 2.0

В версии SQL Server 2017 CTP 2.0 нет новых функций служб SQL Server Integration Services.

## <a name="new-in-ssis-in-sql-server-2017-ctp-14"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 1.4

В версии SQL Server 2017 CTP 1.4 нет новых функций служб SQL Server Integration Services.

## <a name="new-in-ssis-in-sql-server-2017-ctp-13"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 1.3

В версии SQL Server 2017 CTP 1.3 нет новых функций служб SQL Server Integration Services.

## <a name="new-in-ssis-in-sql-server-2017-ctp-12"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 1.2

В версии SQL Server 2017 CTP 1.2 нет новых функций служб SQL Server Integration Services.

## <a name="new-in-ssis-in-sql-server-2017-ctp-11"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 1.1

В версии SQL Server 2017 CTP 1.1 нет новых функций служб SQL Server Integration Services.

## <a name="new-in-ssis-in-sql-server-2017-ctp-10"></a>Новые возможности служб SQL Server Integration Services в SQL Server 2017 CTP 1.0

### <a name="scale-out-for-ssis"></a>Масштабное развертывание для служб SQL Server Integration Services

Функция масштабного развертывания значительно упрощает выполнение [!INCLUDE[ssIS_md](../includes/ssis-md.md)] на нескольких компьютерах. 
   
После установки масштаба главной и рабочих ролей масштабного развертывания пакет можно распространить для автоматического выполнения в различных рабочих ролях. Если происходит непредвиденная остановка выполнения, повторная попытка предпринимается автоматически. Кроме того, всеми выполнениями и рабочими ролями можно централизованно управлять с помощью главной роли.
   
Дополнительные сведения см. в разделе [Масштабное развертывание служб Integration Services](../integration-services/scale-out/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Поддержка ресурсов Microsoft Dynamics Online

Источник OData и диспетчер подключений OData теперь поддерживают подключение к каналам OData в Microsoft Dynamics AX Online и Microsoft Dynamics CRM Online.

