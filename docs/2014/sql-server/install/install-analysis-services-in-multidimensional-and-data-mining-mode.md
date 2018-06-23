---
title: Установка служб Analysis Services в многомерном и модели интеллектуального анализа данных | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
caps.latest.revision: 47
author: HeidiSteen
ms.author: heidist
manager: jhubbard
ms.openlocfilehash: 1a35dae4817d38ea3485b8b34a493314302bdfa0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192616"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a>Установка служб Analysis Services в многомерном режиме и режиме интеллектуального анализа данных
  Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляют средства оперативной аналитической обработки (OLAP) и средства интеллектуального анализа данных для приложений бизнес-аналитики. В этом выпуске поддержка баз данных OLAP и моделями интеллектуального анализа данных доступен при установке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в *многомерном режиме*. Многомерный режим — один из трех серверных режимов, в котором работают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это режим по умолчанию. При установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] со значениями по умолчанию получится экземпляр, работающий с многомерными базами данных и моделями интеллектуального анализа данных.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — Это функция нескольких экземпляров, это означает, что можно установить несколько экземпляров [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на одном компьютере или запустите новый экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] side-by-side более ранней версии. Серверный режим выбирается на уровне конкретного экземпляра. Использование других режимов требует установки дополнительных экземпляров сервера.  
  
 Можно установить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] отдельно или с другими компонентами. Если установить только [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], следующие функции, которые устанавливаются при выборе **служб Analysis Services** на странице выбора компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастера установки:  
  
-   Сервер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для запуска баз данных и моделей интеллектуального анализа данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   Поставщики данных, используемые для доступа служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] к базам данных-источникам  
  
-   Диспетчер конфигурации SQL Server  
  
## <a name="choosing-additional-features"></a>Выбор дополнительных функций  
 Для разработки решений OLAP и хранилищ данных служб Analysis Services необходимо установить дополнительные компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обеспечивающие возможности разработки, развертывания и администрирования баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Следующие дополнительные возможности могут применяться во многих типичных пользовательских сценариях.  
  
-   Среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] используется для создания и просмотра структур данных и моделей интеллектуального анализа данных в службах Analysis Services.  
  
-   Средства связи клиентских компонентов, используются для взаимодействия между клиентами и серверами, включая сетевые библиотеки для DB-Library, ODBC и OLE DB.  
  
-   Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], набор графических и программируемых объектов для перемещения, копирования и преобразования данных.  
  
-   Средства управления, включая диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и монитор репликации.  
  
## <a name="installation-tasks"></a>Задачи установки  
 К задачам установки относятся следующие.  
  
|Ссылки|Задания|  
|-----------|-----------|  
|[Оборудованию и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) и [Настройка учетных записей служб Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).|Перед запуском программы установки проверьте предварительные условия для установки служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и определите учетную запись, которая будет использоваться для сервера.|  
|[Установка с помощью мастера установки SQL Server 2014 &#40;установки&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).|Запустите программу установки SQL Server, чтобы установить программное обеспечение.|  
|[Настройка брандмауэра Windows для разрешения доступа к службам Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|После завершения установки следует настроить параметры брандмауэра, чтобы разрешить удаленные соединения с сервером.|  
|[Предоставление доступа к объектам и операциям (службы Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)|Пользователи, которым требуется доступ к базам данных служб Analysis Services, должны иметь разрешение на чтение по крайней мере для одной базы данных на сервере.|  
  
## <a name="related-content"></a>См. также  
 Дополнительное содержимое по настройке можно найти в следующих разделах:  
  
 [Установка служб Analysis Services в табличном режиме](../../analysis-services/instances/install-windows/install-analysis-services.md)  
  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
 [Надстройки интеллектуального анализа данных SQL Server](http://go.microsoft.com/fwlink/?LinkId=197091)  
  
 По умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы баз данных, образцы кода и надстройки клиентских приложений не устанавливаются. Дополнительные сведения об установке образцов баз данных и образцов кода см. на [веб-сайте CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>См. также  
 [Возможности, поддерживаемые различными выпусками SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473)   
 [Языки и параметры сортировки &#40;служб Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md)   
 [Обновление служб Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  