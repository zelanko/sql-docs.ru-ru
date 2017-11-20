---
title: "SQL Server Integration Services (SSIS) масштабирования рабочей | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 77cf90268938bada458aa159a5f18f885491b407
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out-worker"></a>Рабочая роль масштабного развертывания служб Integration Services (SSIS)

Масштаб Out работник создает [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] служба шкалы Out Worker запросу выполнение задачи из шкалы Out главного и выполняет пакеты локально с ISServerExec.exe.

## <a name="configure-sql-server-integration-services-scale-out-worker-service"></a>Настройка службы рабочей роли масштабного развертывания для SQL Server Integration Services
Службу рабочей роли масштабного развертывания можно настроить с помощью файла \<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config. После обновления файла конфигурации следует перезапустить службу.

Конфигурация  |Description  |Значение по умолчанию  
---------|---------|---------
DisplayName|Отображаемое имя рабочей роли масштабного развертывания. **Неиспользуемые в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 г.**|Имя компьютера         
Description|Описание рабочей роли масштабного развертывания. **Неиспользуемые в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 г.**|Пустой         
MasterEndpoint|Конечная точка для подключения к главной роли масштабного развертывания.|Конечная точка, заданная во время установки рабочей роли масштабного развертывания         
MasterHttpsCertThumbprint|Отпечаток клиентского SSL-сертификата, используемый для проверки подлинности главной роли масштабного развертывания|Отпечаток клиентского сертификата, указанный во время установки рабочей роли масштабного развертывания.          
WorkerHttpsCertThumbprint|Отпечаток сертификата для главной роли масштабного развертывания, использованный для проверки подлинности рабочей роли масштабного развертывания.|Отпечаток сертификата, созданный и установленный автоматически при установке рабочей роли масштабного развертывания          
StoreLocation|Расположение для хранения сертификата рабочей роли.|LocalMachine       
StoreName|Имя хранилища, где находится сертификат рабочей роли.|My         
AgentHeartbeatInterval|Интервал пульса для рабочей роли масштабного развертывания.|00:01:00         
TaskHeartbeatInterval|Интервал вывода состояния задачи для рабочей роли масштабного развертывания.|00:00:10         
HeartbeatErrorTollerance|По истечении этого периода после последнего успешного пульса задачи она прекращается, если в ответе пульса возвращается ошибка.|00:10:00      
TaskRequestMaxCPU|Верхний предел ресурсов ЦП для запроса задач рабочей ролью масштабного развертывания. **Неиспользуемые в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 г.**|70.0         
TaskRequestMinMemory|Нижний предел объекта памяти в МБ для запроса задач рабочей ролью масштабного развертывания. **Неиспользуемые в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2017 г.**|100.0         
MaxTaskCount|Максимальное число задач, которое может вмещать в себя рабочая роль масштабного развертывания.|10         
LeaseInternval|Интервал аренды для задачи, содержащейся в рабочей роли масштабного развертывания.|00:01:00         
TasksRootFolder|Папка журналов задач. При пустом значении используется путь \<диск\>:\Users\\*[учетная_запись]*\AppData\Local\SSIS\Cluster\Tasks. Папка [учетная_запись] соответствует учетной записи, с помощью которой выполняется служба рабочей роли масштабного развертывания. По умолчанию используется учетная запись SSISScaleOutWorker140.|Пустой         
TaskLogLevel|Уровень ведения журнала задач для рабочей роли масштабного развертывания. (Verbose 0x01, Information 0x02, Warning 0x04, Error 0x08, Progress 0x10, CriticalError 0x20, Audit 0x40)|126 (Information,Warning,Error,Progress,CriticalError,Audit)     
TaskLogSegment|Интервал времени для файла журнала задач.|00:00:00         
TaskLogEnabled|Указывает, включен ли журнал задач.|true         
ExecutionLogCacheFolder|Папка, используемая для кэширования журнала выполнения пакета. При пустом значении используется путь \<диск\>:\Users\\*[учетная_запись]*\AppData\Local\SSIS\Cluster\Agent\ELogCache. Папка [учетная_запись] соответствует учетной записи, с помощью которой выполняется служба рабочей роли масштабного развертывания. По умолчанию используется учетная запись SSISScaleOutWorker140.|Пустой         
ExecutionLogMaxBufferLogCount|Максимальное количество кэшированных журналов выполнения кэширования в одном буфере в памяти.|10000        
ExecutionLogMaxInMemoryBufferCount|Максимальное количество буферов журналов выполнения в памяти.|10         
ExecutionLogRetryCount|Число повторных попыток при сбое ведения журнала выполнения.|3
ExecutionLogRetryTimeout|Время ожидания повтора при сбое ведения журнала выполнения. Если достигнут ExecutionLogRetryTimeout ExecutionLogRetryCount игнорируется.|7.00:00:00 (7 дней)        
AgentId|Идентификатор агента рабочей роли для рабочей роли масштабного развертывания|Автоматическое создание        

## <a name="view-scale-out-worker-log"></a>Просмотр журнала рабочей роли масштабного развертывания
Файл журнала шкалы Out рабочая служба находится в \<драйвер\>: \Users\\*[счет]*\AppData\Local\SSIS\ScaleOut\Agent путь к папке.

Расположение журнала для каждой отдельной задачи настраивается в файле WorkerSettings.config процессом TasksRootFolder. Если он не указан, журнал находится в \<драйвер\>: \Users\\*[счет]*\AppData\Local\SSIS\ScaleOut\Tasks путь к папке. 

*[Счет]* является учетной записи службы шкалы Out работника. По умолчанию используется учетная запись SSISScaleOutWorker140.

