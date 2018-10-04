---
title: Установка служб Analysis Services в многомерном и модели интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 92460328b9d85ab5818679b12639618ffe2b0a14
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149904"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a>Установка служб Analysis Services в многомерном режиме и режиме интеллектуального анализа данных
  Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляют средства оперативной аналитической обработки (OLAP) и средства интеллектуального анализа данных для приложений бизнес-аналитики. В этом выпуске поддержка баз данных OLAP и моделями интеллектуального анализа данных доступна при установке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в *многомерном режиме*. Многомерный режим — один из трех серверных режимов, в котором работают службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это режим по умолчанию. При установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] со значениями по умолчанию получится экземпляр, работающий с многомерными базами данных и моделями интеллектуального анализа данных.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — Это функция несколькими экземплярами, это означает, что вы можете установить несколько экземпляров [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на одном компьютере, или запустить новый экземпляр класса [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] side-by-side более ранней версии. Серверный режим выбирается на уровне конкретного экземпляра. Использование других режимов требует установки дополнительных экземпляров сервера.  
  
 Можно установить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] отдельно или с другими компонентами. Если просто установить [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], будут установлены следующие компоненты, при выборе **служб Analysis Services** на странице выбора компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер установки:  
  
-   Сервер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для запуска баз данных и моделей интеллектуального анализа данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   Поставщики данных, используемые для доступа служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] к базам данных-источникам  
  
-   Диспетчер конфигурации SQL Server  
  
## <a name="choosing-additional-features"></a>Выбор дополнительных функций  
 Для разработки решений OLAP и хранилищ данных служб Analysis Services необходимо установить дополнительные компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обеспечивающие возможности разработки, развертывания и администрирования баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Следующие дополнительные возможности могут применяться во многих типичных пользовательских сценариях.  
  
-   Среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] используется для создания и просмотра структур данных и моделей интеллектуального анализа данных в службах Analysis Services.  
  
-   Компоненты связи клиентских средств, используемый для обмена данными между клиентами и серверами, включая сетевые библиотеки для DB-Library, ODBC и OLE DB.  
  
-   Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], набор графических и программируемых объектов для перемещения, копирования и преобразования данных.  
  
-   Средства управления, включая диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и монитор репликации.  
  
## <a name="installation-tasks"></a>Задачи установки  
 К задачам установки относятся следующие.  
  
|Ссылки|Задания|  
|-----------|-----------|  
|[Оборудованию и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) и [Настройка учетных записей служб Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).|Перед запуском программы установки проверьте предварительные условия для установки служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и определите учетную запись, которая будет использоваться для сервера.|  
|[Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).|Запустите программу установки SQL Server, чтобы установить программное обеспечение.|  
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
  
  
