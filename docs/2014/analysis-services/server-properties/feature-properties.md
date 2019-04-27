---
title: Свойства компонента | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c9047bc6bae67b005d8ed93e4831557a0dac9b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746906"
---
# <a name="feature-properties"></a>Свойства компонента
  Свойства функций служат для настройки возможностей продуктов, большинство из них являются расширенными, включая свойства, которые управляют связями между экземплярами сервера.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера, перечисленные в следующей таблице. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Применимо к:** Только многомерный режим сервера  
  
## <a name="properties"></a>Свойства  
  
|Свойство|По умолчанию|Описание|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|1|Логическое свойство, показывающее, включены ли процедуры хранилища среды CLR.|  
|`LinkInsideInstanceEnabled`|1|Логическое свойство, показывающее, может ли связанный объект быть создан в том же экземпляре сервера.|  
|`LinkToOtherInstanceEnabled`|0|Логическое свойство, показывающее, можно ли связываться с объектами на удаленных серверах.|  
|`LinkFromOtherInstanceEnabled`|0|Логическое свойство, показывающее, могут ли объекты связываться с других экземпляров сервера.|  
|`ConnStringEncryptionEnabled`|1|Логическое свойство, показывающее, шифруется ли строка соединения в файле конфигурации сервера.|  
|`UseCachedPageAllocators`|0|Логическое свойство, показывающее, включены ли механизмы выделения кэшированных страниц.|  
|`ComUdfEnabled`|0|Логическое свойство, показывающее, включены ли определяемые пользователем функции, определенные в виде COM-объектов.|  
|`SQMSupportEnabled`|1|Свойство логического типа, показывающее, отправляются ли отчеты об ошибках и использовании компонентов в корпорацию [!INCLUDE[msCoName](../../includes/msconame-md.md)] автоматически.|  
|`ResourceMonitoringEnabled`|1|Свойство логического типа, показывающее, включены ли счетчики мониторинга внутренних ресурсов. По умолчанию это свойство включено. Будучи включенным, это свойство позволяет счетчикам выполнять сбор данных об использовании ЦП, памяти и работе подсистемы ввода-вывода.<br /><br /> Счетчики мониторинга внутренних ресурсов используются динамическими административными представлениями (DMV), которые предоставляют информацию об использовании ресурсов. Если отключить это свойство, то запросы динамического административного представления по-прежнему будут выполняться, но собранные результаты будут недействительными. Динамические административные представления, зависящие от этого свойства:<br />**DISCOVER_OBJECT_ACTIVITY**<br />**DISCOVER_COMMAND_OBJECTS**<br />**DISCOVER_SESSIONS** (для SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> В многоядерной системе с архитектурой NUMA отключение этого свойства может повысить производительность запросов, особенно при высоких многопользовательских рабочих нагрузках. Следует выполнить сравнительные проверки для определения того, можно ли повысить производительность выполнения запросов в результате изменения этого свойства. Рекомендации по выполнению сравнительных проверок (включая способы очистки кэша и предотвращения распространенных ошибок) см. в [руководстве по использованию служб SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Использование динамических административных представлений для мониторинга служб Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
