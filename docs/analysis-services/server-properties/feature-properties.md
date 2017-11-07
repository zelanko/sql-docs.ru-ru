---
title: "Свойства компонента | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5249b93411e921ba98f23ccd99fe4d3ea475a6ce
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="feature-properties"></a>Свойства функций
  Свойства функций служат для настройки возможностей продуктов, большинство из них являются расширенными, включая свойства, которые управляют связями между экземплярами сервера.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера, перечисленные в следующей таблице. Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Область применения:** только в многомерном режиме сервера  
  
## <a name="properties"></a>Свойства  
  
|Свойство|По умолчанию|Description|  
|--------------|-------------|-----------------|  
|**ManagedCodeEnabled**|1|Логическое свойство, показывающее, включены ли процедуры хранилища среды CLR.|  
|**LinkInsideInstanceEnabled**|1|Логическое свойство, показывающее, может ли связанный объект быть создан в том же экземпляре сервера.|  
|**LinkToOtherInstanceEnabled**|0|Логическое свойство, показывающее, можно ли связываться с объектами на удаленных серверах.|  
|**LinkFromOtherInstanceEnabled**|0|Логическое свойство, показывающее, могут ли объекты связываться с других экземпляров сервера.|  
|**ConnStringEncryptionEnabled**|1|Логическое свойство, показывающее, шифруется ли строка соединения в файле конфигурации сервера.|  
|**UseCachedPageAllocators**|0|Логическое свойство, показывающее, включены ли механизмы выделения кэшированных страниц.|  
|**ComUdfEnabled**|0|Логическое свойство, показывающее, включены ли определяемые пользователем функции, определенные в виде COM-объектов.|  
|**SQMSupportEnabled**|1|Свойство логического типа, показывающее, отправляются ли отчеты об ошибках и использовании компонентов в корпорацию [!INCLUDE[msCoName](../../includes/msconame-md.md)] автоматически.|  
|**ResourceMonitoringEnabled**|1|Свойство логического типа, показывающее, включены ли счетчики мониторинга внутренних ресурсов. По умолчанию это свойство включено. Будучи включенным, это свойство позволяет счетчикам выполнять сбор данных об использовании ЦП, памяти и работе подсистемы ввода-вывода.<br /><br /> Счетчики мониторинга внутренних ресурсов используются динамическими административными представлениями (DMV), которые предоставляют информацию об использовании ресурсов. Если отключить это свойство, то запросы динамического административного представления по-прежнему будут выполняться, но собранные результаты будут недействительными. Динамические административные представления, зависящие от этого свойства:<br /><br /> **DISCOVER_OBJECT_ACTIVITY**<br /><br /> **DISCOVER_COMMAND_OBJECTS**<br /><br /> **DISCOVER_SESSIONS** (для SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Примечание. В многоядерной системе с архитектурой NUMA отключение этого свойства может повысить производительность запросов, особенно при высоких многопользовательских рабочих нагрузках. Следует выполнить сравнительные проверки для определения того, можно ли повысить производительность выполнения запросов в результате изменения этого свойства. Рекомендации по выполнению сравнительных проверок (включая способы очистки кэша и предотвращения распространенных ошибок) см. в [руководстве по использованию служб SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>См. также  
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Использование динамических административных представлений для мониторинга служб Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

