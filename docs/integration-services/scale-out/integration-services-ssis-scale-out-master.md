---
title: Мастер горизонтального увеличения масштаба | Документация Майкрософт
description: В этой статье описывается компонент "Мастер горизонтального увеличения масштаба" в развертывании SSIS с горизонтальным увеличением масштаба
ms.custom: performance
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: e7d9bc5b6d84a0108fd68a77a06bcbda5bf47d44
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919003"
---
# <a name="integration-services-ssis-scale-out-master"></a>Главная роль горизонтального увеличения масштаба служб Integration Services (SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]



Мастер горизонтального увеличения масштаба управляет системой горизонтального увеличения масштаба посредством каталога SSISDB и службы мастера горизонтального увеличения масштаба. 

Каталог SSISDB хранит все данные для рабочих ролей горизонтального увеличения масштаба, пакетов и выполнений. Он обеспечивает интерфейс для использования рабочей роли и выполнения пакетов в развертывании с горизонтальным увеличением масштаба. См. дополнительные сведения в руководствах по [ настройке развертывания служб Integration Services с горизонтальным увеличением масштаба](walkthrough-set-up-integration-services-scale-out.md) и [выполнению пакетов в службах Integration Services](run-packages-in-integration-services-ssis-scale-out.md).

Служба мастера горизонтального увеличения масштаба — это служба Windows, отвечающая за взаимодействие с рабочими ролями горизонтального увеличения масштаба. Она возвращает состояние выполнения пакетов рабочими ролями горизонтального увеличения масштаба по протоколу HTTPS и обрабатывает данные в SSISDB. 

## <a name="scale-out-views-and-stored-procedures-in-ssisdb"></a>Хранимые процедуры и представления горизонтального увеличения масштаба в SSISDB

### <a name="views"></a>Представления

- [[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md)
- [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md)

### <a name="stored-procedures"></a>Хранимые процедуры

- Для управления рабочими ролями горизонтального увеличения масштаба:
    - [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md)
    - [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md)

- Для выполнения пакетов в развертывании с горизонтальным увеличением масштаба:
    - [[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)
    - [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)
    - [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)

## <a name="configure-the-scale-out-master-service"></a>Настройка службы мастера горизонтального увеличения масштаба

Служба мастера горизонтального увеличения масштаба настраивается с помощью файла `<drive>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config`. После изменения файла конфигурации следует перезапустить службу.


|Конфигурация  |Описание  |Значение по умолчанию  |
|---------|---------|---------|
|PortNumber|Номер сетевого порта, используемый для взаимодействия с рабочей ролью горизонтального увеличения масштаба.|8391|
|SSLCertThumbprint|Отпечаток TLS/SSL-сертификата, используемый для защиты взаимодействия с рабочей ролью горизонтального увеличения масштаба.|Отпечаток TLS/SSL-сертификата, указанный во время установки главной роли горизонтального увеличения масштаба|
|SqlServerName|Имя [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], содержащего каталог SSISDB. Например, ServerName\\InstanceName.|Имя SQL Server, устанавливаемого вместе с мастером горизонтального увеличения масштаба.|
|CleanupCompletedJobsIntervalInMs|Интервал очистки завершенных заданий выполнения в миллисекундах.|43200000|
|DealWithExpiredTasksIntervalInMs|Интервал обработки завершенных заданий выполнения в миллисекундах.|300000|
|MasterHeartbeatIntervalInMs|Интервал для пульса главной роли горизонтального увеличения масштаба в миллисекундах. Это свойство указывает интервал, с которым мастер горизонтального увеличения масштаба обновляет свое состояние в каталоге SSISDB.|30 000|
|SqlConnectionTimeoutInSecs|Время ожидания соединения SQL в секундах при подключении к SSISDB.|15|
||||    

## <a name="view-the-scale-out-master-service-log"></a>Просмотр журнала службы мастера горизонтального увеличения масштаба

Файл журнала для службы мастера горизонтального увеличения масштаба находится в папке `<drive>:\Users\[account]\AppData\Local\SSIS\ScaleOut\Master`. 

Параметр *[account]* соответствует учетной записи, с помощью которой выполняется служба мастера горизонтального увеличения масштаба. По умолчанию это учетная запись `SSISScaleOutMaster140`.

## <a name="next-steps"></a>Дальнейшие действия

[Рабочая роль горизонтального увеличения масштаба служб Integration Services (SSIS)](integration-services-ssis-scale-out-worker.md)
