---
title: Мастер SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье описывается компонент "Мастер Scale Out" в SSIS Scale Out.
ms.custom: performance
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
ms.openlocfilehash: e3e52a854224210ed4561dbce12877fbb4c0f6fb
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68082125"
---
# <a name="integration-services-ssis-scale-out-master"></a>Главная роль масштабного развертывания служб Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Мастер Scale Out управляет системой Scale Out посредством каталога SSISDB и службы мастера Scale Out. 

Каталог SSISDB хранит все данные для рабочих ролей Scale Out, пакетов и выполнений. Он обеспечивает интерфейс для использования рабочей роли и выполнения пакетов в масштабном развертывании. См. дополнительные сведения в руководствах по [ настройке масштабного развертывания Integration Services](walkthrough-set-up-integration-services-scale-out.md) и [выполнению пакетов в службах Integration Services](run-packages-in-integration-services-ssis-scale-out.md).

Служба мастера Scale Out — это служба Windows, отвечающая за взаимодействие с рабочими ролями Scale Out. Она возвращает состояние выполнения пакетов рабочими ролями Scale Out по протоколу HTTPS и обрабатывает данные в SSISDB. 

## <a name="scale-out-views-and-stored-procedures-in-ssisdb"></a>Хранимые процедуры и представления Scale Out в SSISDB

### <a name="views"></a>Представления

- [[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md)
- [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md)

### <a name="stored-procedures"></a>Хранимые процедуры

- Для управления рабочими ролями Scale Out:
    - [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md)
    - [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md)

- Для выполнения пакетов в Scale Out:
    - [[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)
    - [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)
    - [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)

## <a name="configure-the-scale-out-master-service"></a>Настройка службы мастера Scale Out

Служба мастера Scale Out настраивается с помощью файла `<drive>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config`. После изменения файла конфигурации следует перезапустить службу.


|Конфигурация  |Описание  |Значение по умолчанию  |
|---------|---------|---------|
|PortNumber|Номер сетевого порта, используемый для взаимодействия с рабочей ролью масштабного развертывания.|8391|
|SSLCertThumbprint|Отпечаток SSL-сертификата, используемый для защиты взаимодействия с рабочей ролью масштабного развертывания.|Отпечаток SSL-сертификата, указанный во время установки главной роли масштабного развертывания|
|SqlServerName|Имя [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], содержащего каталог SSISDB. Например, ServerName\\InstanceName.|Имя SQL Server, устанавливаемого вместе с мастером Scale Out.|
|CleanupCompletedJobsIntervalInMs|Интервал очистки завершенных заданий выполнения в миллисекундах.|43200000|
|DealWithExpiredTasksIntervalInMs|Интервал обработки завершенных заданий выполнения в миллисекундах.|300000|
|MasterHeartbeatIntervalInMs|Интервал для пульса главной роли масштабного развертывания в миллисекундах. Это свойство указывает интервал, с которым мастер Scale Out обновляет свое состояние в каталоге SSISDB.|30 000|
|SqlConnectionTimeoutInSecs|Время ожидания соединения SQL в секундах при подключении к SSISDB.|15|
||||    

## <a name="view-the-scale-out-master-service-log"></a>Просмотр журнала службы мастера Scale Out

Файл журнала для службы мастера Scale Out находится в папке `<drive>:\Users\[account]\AppData\Local\SSIS\ScaleOut\Master`. 

Параметр *[account]* соответствует учетной записи, с помощью которой выполняется служба мастера Scale Out. По умолчанию это учетная запись `SSISScaleOutMaster140`.

## <a name="next-steps"></a>Дальнейшие действия

[Рабочая роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-worker.md)
