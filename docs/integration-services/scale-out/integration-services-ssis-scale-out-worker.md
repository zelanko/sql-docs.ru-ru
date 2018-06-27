---
title: Рабочая роль SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье описывается компонент "Мастер Scale Out" в SSIS Scale Out.
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 2949f0aabaf4f59d6d2fc6635991f8eb0a921ca6
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35408126"
---
# <a name="integration-services-ssis-scale-out-worker"></a>Рабочая роль масштабного развертывания служб Integration Services (SSIS)

Рабочая роль Scale Out запускает службу рабочей роли Scale Out для получения задач выполнения из мастера Scale Out. Затем рабочая роль выполняет пакеты локально с помощью `ISServerExec.exe`.

## <a name="configure-the-scale-out-worker-service"></a>Настройка службы рабочей роли Scale Out
Службу рабочей роли Scale Out можно настроить с помощью файла ` \<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config`. После изменения файла конфигурации следует перезапустить службу.

Конфигурация  |Описание  |Значение по умолчанию  
---------|---------|---------
DisplayName|Отображаемое имя рабочей роли масштабного развертывания. **НЕ ИСПОЛЬЗУЕТСЯ в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017.**|Имя компьютера         
Описание|Описание рабочей роли масштабного развертывания. **НЕ ИСПОЛЬЗУЕТСЯ в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017.**|Пустой         
MasterEndpoint|Конечная точка для подключения к главной роли масштабного развертывания.|Конечная точка, заданная во время установки рабочей роли масштабного развертывания         
MasterHttpsCertThumbprint|Отпечаток клиентского SSL-сертификата, используемый для проверки подлинности главной роли масштабного развертывания|Отпечаток клиентского сертификата, указанный во время установки рабочей роли масштабного развертывания.          
WorkerHttpsCertThumbprint|Отпечаток сертификата для главной роли масштабного развертывания, использованный для проверки подлинности рабочей роли масштабного развертывания.|Отпечаток сертификата, созданный и установленный автоматически при установке рабочей роли масштабного развертывания          
StoreLocation|Расположение для хранения сертификата рабочей роли.|LocalMachine       
StoreName|Имя хранилища, где находится сертификат рабочей роли.|My         
AgentHeartbeatInterval|Интервал пульса для рабочей роли масштабного развертывания.|00:01:00         
TaskHeartbeatInterval|Интервал вывода состояния задачи для рабочей роли масштабного развертывания.|00:00:10         
HeartbeatErrorTollerance|По истечении этого периода после последнего успешного пульса задачи она прекращается, если в ответе пульса возвращается ошибка.|00:10:00      
TaskRequestMaxCPU|Верхний предел ресурсов ЦП для запроса задач рабочей ролью масштабного развертывания.|70.0         
TaskRequestMinMemory|Нижний предел объекта памяти в МБ для запроса задач рабочей ролью масштабного развертывания.|100.0         
MaxTaskCount|Максимальное число задач, которое может вмещать в себя рабочая роль масштабного развертывания.|10         
LeaseInternval|Интервал аренды для задачи, содержащейся в рабочей роли масштабного развертывания.|00:01:00         
TasksRootFolder|Папка журналов задач. Если значение не указано, используется путь к папке `\<drive\>:\Users\[account]\AppData\Local\SSIS\Cluster\Tasks`. Папка [учетная_запись] соответствует учетной записи, с помощью которой выполняется служба рабочей роли масштабного развертывания. По умолчанию используется учетная запись SSISScaleOutWorker140.|Пустой         
TaskLogLevel|Уровень ведения журнала задач для рабочей роли масштабного развертывания. (Verbose 0x01, Information 0x02, Warning 0x04, Error 0x08, Progress 0x10, CriticalError 0x20, Audit 0x40)|126 (Information, Warning, Error, Progress, CriticalError, Audit)     
TaskLogSegment|Интервал времени для файла журнала задач.|00:00:00         
TaskLogEnabled|Указывает, включен ли журнал задач.|true         
ExecutionLogCacheFolder|Папка, используемая для кэширования журнала выполнения пакета. Если значение не указано, используется путь к папке ` \<drive\>:\Users\[account]\AppData\Local\SSIS\Cluster\Agent\ELogCache`. Папка [учетная_запись] соответствует учетной записи, с помощью которой выполняется служба рабочей роли масштабного развертывания. По умолчанию используется учетная запись SSISScaleOutWorker140.|Пустой         
ExecutionLogMaxBufferLogCount|Максимальное количество кэшированных журналов выполнения кэширования в одном буфере в памяти.|10000        
ExecutionLogMaxInMemoryBufferCount|Максимальное количество буферов журналов выполнения в памяти.|10         
ExecutionLogRetryCount|Число повторных попыток при сбое ведения журнала выполнения.|3
ExecutionLogRetryTimeout|Время ожидания повторных попыток при сбое ведения журнала выполнения. Если достигнуто значение ExecutionLogRetryTimeout, значение ExecutionLogRetryCount игнорируется. |7.00:00:00 (7 дней)        
AgentId|Идентификатор агента рабочей роли для рабочей роли Scale Out|Автоматическое создание    
||||    

## <a name="view-the-scale-out-worker-log"></a>Просмотр журнала рабочей роли Scale Out
Файл журнала для службы рабочей роли Scale Out находится в папке `\<drive\>:\Users\\[account]\AppData\Local\SSIS\ScaleOut\Agent`.

Расположение журнала для каждой отдельной задачи настраивается в файле `WorkerSettings.config` в `TasksRootFolder`. Если значение не задано, журнал находится в папке `\<drive\>:\Users\\[account]\AppData\Local\SSIS\ScaleOut\Tasks`. 

Параметр *[account]* соответствует учетной записи, с помощью которой выполняется служба рабочей роли Scale Out. По умолчанию используется учетная запись `SSISScaleOutWorker140`.

## <a name="next-steps"></a>Следующие шаги
[Главная роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-master.md)
