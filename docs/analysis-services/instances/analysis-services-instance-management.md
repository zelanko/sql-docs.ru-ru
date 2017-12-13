---
title: "Управление экземпляром служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0455fa4f-b92d-4a8b-a8f0-f2a268a5c84e
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 6bdd35da02c1679607ce89002a6a2c3edc569c0c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="analysis-services-instance-management"></a>Управление экземплярами служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Экземпляр служб Analysis Services является копией **msmdsrv.exe** исполняемый файл, который запускается как служба операционной системы. Каждый экземпляр полностью независим от других экземпляров на том же сервере и обладает собственной конфигурацией, разрешениями, портами, стартовыми учетными записями, областью хранения файлов и свойствами режима сервера.  
  
 В контексте безопасности определенной учетной записи входа каждый экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] запускается как служба Windows, Msmdsrv.exe.  
  
-   Имя службы экземпляра по умолчанию служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — MSSQLServerOLAPService.  
  
-   Имя службы каждого именованного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — MSOLAP$InstanceName.  
  
> [!NOTE]  
>  При установке нескольких экземпляров служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] программа установки также устанавливает службу перенаправления, встроенную в службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Служба перенаправления отвечает за направление клиентов на соответствующий именованный экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда запускается в контексте безопасности учетной записи локальной службы — учетной записи пользователя с ограниченными правами, которая используется Windows для системных служб, не получающих доступ к ресурсам за пределами локального компьютера.  
  
 Можно создать конфигурацию с масштабным развертыванием из нескольких экземпляров сервера отчетов, установленных на одном компьютере. В частности, для служб Analysis Services это означает, что можно организовать поддержку различных режимов сервера за счет запуска нескольких экземпляров на одном и том же сервере, каждый из которых может быть настроен на работу в определенном режиме.  
  
 Режим сервера — это свойство, которое определяет архитектуру организации хранилища и использования памяти для конкретного экземпляра. Сервер, работающий в многомерном режиме, использует слой управления ресурсами, созданный для баз данных многомерных кубов и моделей интеллектуального анализа данных. В отличие от этого, в табличном режиме сервера используется подсистема аналитики в памяти VertiPaq и сжатие данных для статистической обработки данных при выполнении запросов.  
  
 Различия в архитектуре хранения и использования памяти означают, что на одном экземпляре служб Analysis Services будут запускаться либо табличные базы данных, либо многомерные базы данных, но не оба типа одновременно. Свойство «Режим сервера» определяет тип базы данных, запущенной в этом экземпляре.  
  
 Режим сервера включается во время установки, если указать тип базы данных, которая будет выполняться на сервере. Чтобы обеспечить поддержку всех доступных режимов, можно установить несколько экземпляров служб Analysis Services на одном и том же сервере, каждый из которых будет настроен на работу в режиме, соответствующем строящимся проектам.  
  
 Как правило, большинство необходимых административных задач можно выполнить в одном режиме. Системный администратор служб Analysis Services может с помощью одних тех же процедур и скриптов управлять любым экземпляром Analysis Services в сети, вне зависимости от типа установки.  
  
> [!NOTE]  
>  Единственным исключением является [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint. Администрирование развернутой на сервере системы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] всегда осуществляется в контексте фермы SharePoint. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] отличается от других режимов сервера тем, что всегда существует лишь один экземпляр, который управляется либо из центра администрирования SharePoint, либо с помощью средства настройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Подключение [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint к среде SQL Server Management Studio или к среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]возможно, но нежелательно. Ферма SharePoint включает инфраструктуру, выполняющую синхронизацию состояния сервера и отслеживающую доступность сервера. Использование других средств может повлиять на эти операции. Дополнительные сведения об администрировании сервера [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] см. в разделе [Power Pivot для SharePoint (службы SSAS)](../../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Ссылка|Описание задачи|  
|----------|----------------------|  
|[Настройка после установки (службы Analysis Services)](../../analysis-services/instances/post-install-configuration-analysis-services.md)|Описываются обязательные и необязательные задачи, которые завершают или изменяют установку служб Analysis.|  
|[Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)|Описывает свойства строки подключения, клиентские библиотеки, методики проверки подлинности и действия по установке или завершению соединений.|  
|[Наблюдение за экземпляром служб Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)|Описываются средства и способы наблюдения за экземпляром сервера, в том числе сведения об использовании средства отслеживания производительности и приложения SQL Server Profiler.|  
|[Высокий уровень доступности и масштабируемость](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)|В этой статье описаны наиболее часто используемые методы для создания высокодоступных масштабируемых баз данных для служб Analysis Services. |  
|[Сценарии глобализации для служб Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md)|Описывает поддерживаемые языки и параметры сортировки, действия по изменению обоих свойств и рекомендации по настройке и тестированию поведений языка и параметров сортировки.|  
|[Журнал операций в службах Analysis Services](../../analysis-services/instances/log-operations-in-analysis-services.md)|Описывает журналы и способы их настройки.|  
  
  
## <a name="see-also"></a>См. также  
 [Сравнение табличных и многомерных решений (службы SSAS)](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Средства настройки PowerPivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [Настройка и администрирование сервера Power Pivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
