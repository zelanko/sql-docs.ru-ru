---
title: "Какой &#39; новые возможности служб Integration Services в SQL Server 2017 г. | Документы Microsoft"
ms.custom: 
ms.date: 07/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 56d4ea145a34048c8619ff88112021f163e26900
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="what39s-new-in-integration-services-in-sql-server-2017"></a>Какой &#39; новые возможности служб Integration Services в SQL Server 2017 г.
В этой статье описаны функции, которые были добавлены или обновлены в [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE]
> 2017 г. SQL Server также включает функции SQL Server 2016 и возможности, добавленные в SQL Server 2016 обновлений. Сведения о новых возможностях служб SQL Server Integration Services в SQL Server 2016 см. в разделе [Новые возможности служб Integration Services в SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="new-in-ssis-in-sql-server-2017-rc1"></a>Новые возможности служб SSIS в SQL Server 2017 г., RC1

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Новые и измененные функции в масштабное развертывание для служб SSIS

-   Мастер масштабирования Scale Out теперь поддерживает высокий уровень доступности. Можно включить Always On для SSISDB и настроить отказоустойчивую кластеризацию для сервера Windows Server, на котором размещена служба шкалы Out главного. Применение этого изменения масштаба Out образец, исключить одну точку сбоя и обеспечения высокого уровня доступности для всего развертывания масштабное развертывание.
-   Улучшена отработка отказа для журналов выполнения из рабочих ролей масштабирования Scale Out. Журналы выполнения сохраняемое на локальном диске, в случае, если шкалы Out работника неожиданно останавливается. Позже после перезагрузки работника перезагружает сохраненные журналы и продолжает сохранять их SSISDB.
-   Параметр *runincluster* хранимой процедуры **[catalog].[create_execution]** переименован в *runinscaleout* для согласованности и удобства чтения. Это изменение имени параметра имеет следующие последствия:
    -   Если у вас есть существующие скрипты для запуска пакетов в масштабное развертывание, необходимо изменить имя параметра с *runincluster* для *runinscaleout* чтобы сделать скрипты, которые работают в версии-кандидата 1.
    -   SQL Server Management Studio (SSMS) 17,1 и более ранних версий не удается запустить выполнение пакета в масштабное развертывание в версии-кандидата 1. Сообщение об ошибке: "*@runincluster* не является параметром процедуры **create_execution**". Эта проблема будет исправлена в следующем выпуске SSMS, в версии 17.2. Версия 17,2 и более поздних версиях SSMS поддерживает новое имя параметра выполнение пакета в масштабное развертывание. До получения версии 17,2 SSMS, чтобы избежать этого, можно использовать имеющиеся версии SSMS, чтобы сформировать скрипт выполнения пакета, а затем изменить имя *runincluster* параметр *runinscaleout* в скрипт и запустите скрипт.
-   Каталог SSIS содержит новое глобальное свойство, позволяющее указать режим по умолчанию для выполнения SSIS-пакетов. Это новое свойство применяется при вызове **[catalog]. [ create_execution]** хранимую процедуру с *runinscaleout* параметр имеет значение null. Этот режим также применяется для задания агента SQL Server SSIS. Новое глобальное свойство можно задать в диалоговом окне Свойства узла SSISDB в среде SSMS или с помощью следующей команды:
    ```sql
    EXEC [catalog].[configure_catalog] @property_name=N'DEFAULT_EXECUTION_MODE', @property_value=1
    ```

## <a name="new-in-ssis-in-sql-server-2017-ctp-21"></a>Новые возможности служб SSIS в SQL Server CTP 2.1 для 2017 г.

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Новые и измененные функции в масштабное развертывание для служб SSIS

-   Теперь вы можете использовать **Use32BitRuntime** параметр во время запуска выполнения в масштабное развертывание.
-   Улучшена производительность для SSISDB ведения журнала для выполнения пакета в масштабное развертывание. Сообщение об ошибке и контекста сообщения журналы теперь записываются SSISDB в пакетном режиме, а не по одному. Ниже приведены дополнительные замечания об этом улучшении.        
    - Некоторые отчеты в текущей версии служб SQL Server Management Studio (SSMS) не в настоящее время отображать эти журналы для выполнений в масштабное развертывание. Мы полагаем, что они будут поддерживаться в следующем выпуске SSMS. Эти отчеты включают *все подключения* отчета, *контекст ошибки* отчета и *сведения о соединении* раздел на панели мониторинга службы интеграции.
    - Новый столбец **event_message_guid** был добавлен. Используйте этот столбец, чтобы присоединить [catalog]. представления [event_message_context] и [catalog]. Просмотр [event_messages] вместо **event_message_id** при выполнении запроса эти журналы выполнений в масштабное развертывание.
-   Чтобы получить это приложение управления для служб SSIS масштабное развертывание, [загрузить SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17,1 или более поздней версии.

## <a name="new-in-ssis-in-sql-server-2017-ctp-20"></a>Новые возможности служб SSIS в SQL Server CTP 2.0 для 2017 г.

Нет новых компонентов служб SSIS в SQL Server 2017 г CTP 2.0.

## <a name="new-in-ssis-in-sql-server-2017-ctp-14"></a>Новые возможности служб SSIS в SQL Server CTP 2017 г. 1.4

Нет новых компонентов служб SSIS в SQL Server 2017 г CTP-версии 1.4.

## <a name="new-in-ssis-in-sql-server-2017-ctp-13"></a>Новые возможности служб SSIS в SQL Server CTP 1.3 для 2017 г.

Нет новых компонентов служб SSIS в SQL Server 2017 г CTP-версии 1.3.

## <a name="new-in-ssis-in-sql-server-2017-ctp-12"></a>Новые возможности служб SSIS в SQL Server CTP 1.2 для 2017 г.

Нет новых компонентов служб SSIS в SQL Server 2017 г CTP-версии 1.2.

## <a name="new-in-ssis-in-sql-server-2017-ctp-11"></a>Новые возможности служб SSIS в SQL Server CTP 2017 г 1.1

Нет новых компонентов служб SSIS в SQL Server 2017 г CTP-версии 1.1.

## <a name="new-in-ssis-in-sql-server-2017-ctp-10"></a>Новые возможности служб SSIS в SQL Server CTP 1.0 для 2017 г.

### <a name="scale-out-for-ssis"></a>Масштабное развертывание для служб SQL Server Integration Services

Функция масштабного развертывания значительно упрощает выполнение [!INCLUDE[ssIS_md](../includes/ssis-md.md)] на нескольких компьютерах. 
   
После установки масштаба главной и рабочих ролей масштабного развертывания пакет можно распространить для автоматического выполнения в различных рабочих ролях. Если происходит непредвиденная остановка выполнения, повторная попытка предпринимается автоматически. Кроме того, всеми выполнениями и рабочими ролями можно централизованно управлять с помощью главной роли.
   
Дополнительные сведения см. в разделе [Масштабное развертывание служб Integration Services](../integration-services/scale-out/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Поддержка ресурсов Microsoft Dynamics Online

Источник OData и диспетчер подключений OData теперь поддерживают подключение к каналам OData в Microsoft Dynamics AX Online и Microsoft Dynamics CRM Online.


