---
title: Справочник по ошибкам и событиям (службы Integration Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, events
- events [Integration Services]
- errors [Integration Services]
- Integration Services, errors
ms.assetid: cf4f0f14-8087-42d7-9b67-e4929228abd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 64e805e5dd9b334afe252e2c1d43685e9c92b95f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71290623"
---
# <a name="errors-and-events-reference-integration-services"></a>Справочник по ошибкам и событиям (службы Integration Services)

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Этот раздел документации содержит сведения о некоторых ошибках и событиях, связанных со службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Сведения о причинах и способах устранения включены в сообщения об ошибках.  
  
 Дополнительные сведения о сообщениях об ошибках служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , включая список большинства ошибок [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с описаниями, см. в статье [Справочник по сообщениям об ошибках служб Integration Services](../integration-services/integration-services-error-and-message-reference.md). Обратите внимание, что в настоящее список время не содержит сведений об устранении ошибок.  
  
> [!IMPORTANT]  
>  Причиной многих ошибок, возникающих при работе служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , являются другие компоненты. Это могут быть поставщики OLE DB и другие компоненты баз данных, например компонент [!INCLUDE[ssDE](../includes/ssde-md.md)] и службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , а также прочие службы и компоненты: файловая система, SMTP-сервер или очередь сообщений Майкрософт. Дополнительные сведения о сообщениях об этих внешних ошибках см. в документации по соответствующему компоненту.  
  
## <a name="error-messages"></a>сообщения об ошибках  
  
|Символическое имя ошибки|Description|  
|----------------------------|-----------------|  
|DTS_E_CACHELOADEDFROMFILE|Указывает, что пакет нельзя выполнить, так как преобразование «Преобразование кэша» пытается записать данные в кэш, хранимый в памяти. Однако диспетчер соединений с кэшем уже загрузил файл кэша в кэш, который находится в памяти.|  
|DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER|Указывает, что невозможно выполнить пакет из-за ошибки указанного соединения.|  
|DTS_E_CANNOTCONVERTBETWEENUNICODEANDNONUNICODESTRINGCOLUMN|Указывает, что компонент потока данных пытается передать строковые данные в Юникоде другому компоненту, ожидающему в соответствующем столбце строковые данные не в Юникоде, или наоборот.|  
|DTS_E_CANNOTCONVERTBETWEENUNICODEANDNONUNICODESTRINGCOLUMNS|Указывает, что компонент потока данных пытается передать строковые данные в Юникоде другому компоненту, ожидающему в соответствующем столбце строковые данные не в Юникоде, или наоборот.|  
|DTS_E_CANTINSERTCOLUMNTYPE|Указывает, что столбец нельзя добавить в таблицу базы данных, так как не поддерживается преобразование между типом данных столбца служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и типом данных столбца базы данных.|  
|DTS_E_CONNECTIONNOTFOUND|Указывает, что не удалось запустить пакет, поскольку не удалось найти указанный диспетчер соединений.|  
|DTS_E_CONNECTIONREQUIREDFORMETADATA|Указывает, что конструктору служб [!INCLUDE[ssIS](../includes/ssis-md.md)] необходимо подключиться к источнику данных для получения новых или обновленных метаданных исходной или целевой базы данных, но установить соединение с источником данных не удалось.|  
|DTS_E_MULTIPLECACHEWRITES|Указывает, что пакет нельзя выполнить, так как преобразование «Преобразование кэша» пытается записать данные в кэш, хранимый в памяти. Однако другое преобразование «Преобразование кэша» уже произвело запись в кэш, находящийся в памяти.|  
|DTS_E_PRODUCTLEVELTOLOW|Указывает, что выполнение пакета невозможно, так как не установлена подходящая версия служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].|  
|DTS_E_READNOTFILLEDCACHE|Указывает, что преобразование «Уточняющий запрос» пытается прочитать данные из кэша памяти в то же время, когда преобразование «Преобразование кэша» записывает данные в кэш.|  
|DTS_E_UNPROTECTXMLFAILED|Указывает, что система не расшифровала защищенный XML-узел.|  
|DTS_E_WRITEWHILECACHEINUSE|Указывает, что преобразование «Преобразование кэша» пытается произвести запись в кэш памяти в то время, как преобразование «Уточняющий запрос» читает данные из кэша памяти.|  
|DTS_W_EXTERNALMETADATACOLUMNSOUTOFSYNC|Указывает, что метаданные столбца в источнике данных не соответствуют метаданным столбца в исходном либо целевом компоненте, подключенном к источнику данных.|  
  
## <a name="events-sqlispackage"></a>События (SQLISPackage)  
 Дополнительные сведения см. в статье [Регистрация событий в пакете служб Integration Services](../integration-services/performance/events-logged-by-an-integration-services-package.md).  
  
|Событие|Description|  
|-----------|-----------------|  
|SQLISPackage_12288|Указывает, что пакет запущен.|  
|SQLISPackage_12289|Указывает, что пакет завершил выполнение успешно.|  
|SQLISPACKAGE_12291|Указывает, что пакет не смог завершить выполнение и был остановлен.|  
|SQLISPackage_12546|Указывает, что задача или другой исполняемый объект пакета завершили свою работу.|  
|SQLISPackage_12549|Указывает, что предупреждение было выдано внутри пакета.|  
|SQLISPackage_12550|Указывает, что сообщение об ошибке было выдано внутри пакета.|  
|SQLISPackage_12551|Указывает, что пакет остановлен, не закончив работу.|  
|SQLISPackage_12557|Указывает, что пакет завершил выполнение.|  
  
## <a name="events-sqlisservice"></a>События (SQLISService)  
 Дополнительные сведения см. в статье [События, зарегистрированные службами Integration Services](../integration-services/service/events-logged-by-the-integration-services-service.md).  
  
|Событие|Description|  
|-----------|-----------------|  
|SQLISService_256|Указывает, что служба запускается.|  
|SQLISService_257|Указывает, что служба уже запущена.|  
|SQLISService_258|Указывает, что служба собирается остановиться.|  
|SQLISService_259|Указывает, что служба уже остановлена.|  
|SQLISService_260|Указывает, что произведена неудачная попытка запустить службу.|  
|SQLISService_272|Указывает, что файл конфигурации не существует в указанном месте.|  
|SQLISService_273|Указывает, что файл конфигурации не может быть прочитан или недопустим.|  
|SQLISService_274|Указывает, что параметр реестра, указывающий местонахождение файла конфигурации, не существует или пуст.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../integration-services/integration-services-error-and-message-reference.md)  
  
  
