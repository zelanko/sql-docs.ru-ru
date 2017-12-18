---
title: "Мастер SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07cd19a5e7a53e824d2bed3a2e2943efd7ef867b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out-master"></a>Главная роль масштабного развертывания служб Integration Services (SSIS)
Главная роль масштабного развертывания управляет системой масштабного развертывания через каталог SSISDB и службу главной роли масштабного развертывания. 

Каталог SSISDB хранит все данные для рабочих ролей масштабного развертывания, пакетов и выполнений. Он обеспечивает интерфейс для использования рабочей роли и выполнения пакетов в масштабном развертывании. Дополнительные сведения см. в статьях [Пошаговое руководство. Настройка масштабного развертывания Integration Services](walkthrough-set-up-integration-services-scale-out.md) и [Выполнение пакетов в службах Integration Services](run-packages-in-integration-services-ssis-scale-out.md).

Служба главной роли масштабного развертывания — это служба Windows, отвечающая за взаимодействие с рабочими ролями масштабного развертывания. Она изменяет состояние выполнения пакетов рабочими ролями по протоколу HTTPS и обрабатывает данные в SSISDB. 

## <a name="scale-out-related-sql-views-and-stored-procedures-in-ssisdb"></a>Связанные с масштабным развертыванием хранимые процедуры и представления SQL в SSISDB

#### <a name="views"></a>Представления:
[[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md), [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md).

#### <a name="stored-procedures"></a>Хранимые процедуры

- Для управления рабочими ролями масштабного развертывания:  
 [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md), [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md).
- Для выполнения пакетов в масштабном развертывании:   
[[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md), [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).   

## <a name="configure-sql-server-integration-services-scale-out-master-service"></a>Настройка службы главной роли масштабного развертывания для SQL Server Integration Services
Службу главной роли масштабного развертывания можно настроить с помощью файла \<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config. После обновления файла конфигурации следует перезапустить службу.


Конфигурация  |Description  |Значение по умолчанию  
---------|---------|---------
PortNumber|Номер сетевого порта, используемый для взаимодействия с рабочей ролью масштабного развертывания.|8391         
SSLCertThumbprint|Отпечаток SSL-сертификата, используемый для защиты взаимодействия с рабочей ролью масштабного развертывания.|Отпечаток SSL-сертификата, указанный во время установки главной роли масштабного развертывания         
SqlServerName|Имя [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], содержащего каталог SSISDB. Пример: ServerName\\\\InstanceName.|Имя SQL Server, устанавливаемого вместе с мастером Scale Out.         
CleanupCompletedJobsIntervalInMs|Интервал очистки завершенных заданий выполнения в миллисекундах.|43200000         
DealWithExpiredTasksIntervalInMs|Интервал обработки завершенных заданий выполнения в миллисекундах.|300000
MasterHeartbeatIntervalInMs|Интервал для пульса главной роли масштабного развертывания в миллисекундах. Указывает интервал, с которым главная роль масштабного развертывания обновляет свое состояние в каталоге SSISDB.|30 000
SqlConnectionTimeoutInSecs|Время ожидания соединения SQL в секундах при подключении к SSISDB.|15        

## <a name="view-scale-out-master-service-log"></a>Просмотр журнала службы главной роли масштабного развертывания
Файл журнала службы главной роли масштабного развертывания находится в папке \<диск\>:\Users\\*[учетная запись]*\AppData\Local\SSIS\ScaleOut\Master. 

Папка *[учетная_запись]* соответствует учетной записи, с помощью которой выполняется служба мастера Scale Out. По умолчанию этой учетной записью является SSISScaleOutMaster140.
