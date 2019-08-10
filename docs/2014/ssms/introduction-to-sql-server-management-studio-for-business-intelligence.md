---
title: Введение в SQL Server Management Studio для бизнес-аналитики | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.assetid: ffaa77b7-03d0-4d7a-aa42-c5091a4f2ceb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a914aeeae889189453b4f4e6f47ebfbcd0fc44c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892277"
---
# <a name="introduction-to-sql-server-management-studio-for-business-intelligence"></a>Введение в среду SQL Server Management Studio для решения задач бизнес-аналитики
  Среда [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] предназначена для доступа к службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], а также для их настройки, администрирования и управления ими. Хотя все три технологии бизнес-аналитики полагаются на среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], административные задачи, связанные с каждой из этих технологий, несколько отличаются.  
  
> [!NOTE]  
>  Чтобы создать и изменить решения [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , воспользуйтесь [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], а не [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] представляет собой среду разработки, основанную на [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Управление решениями Analysis Services в среде SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] позволяет управлять объектами служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , например выполнять их резервное копирование и обработку.  
  
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] позволяет создавать проекты скриптов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , в которых выполняются разработка и сохранение скриптов с использованием многомерных выражений (MDX), расширений интеллектуального анализа данных (DMX) и XML для аналитики (XMLA). Проекты скриптов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] используются для выполнения задач управления или повторного создания баз данных, кубов и других объектов в экземплярах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Например, можно разработать скрипт XMLA в проекте скрипта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , который создает объекты непосредственно в существующем экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Проекты скриптов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] могут быть сохранены в составе решения и интегрироваться с контролем исходного кода.  
  
 Дополнительные сведения об использовании [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]см. в разделе [Analysis Services Scripts Project in SQL Server Management Studio](https://docs.microsoft.com/analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio).  
  
## <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Управление решениями Integration Services в среде SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] позволяет использовать службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для управления пакетами и наблюдения за выполняющимися пакетами. В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] можно организовать пакеты в папки, выполнять, импортировать и экспортировать пакеты, переносить пакеты служб DTS и обновлять пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Управление проектами служб Reporting Service в среде SQL Server Management Studio  
 Среда SQL Server Management Studio позволяет включать компоненты служб Reporting Services, администрировать серверы и базы данных, управлять ролями и заданиями.  
  
 Она реализует функции управления общими расписаниями (в папке «Общие расписания») и базами данных сервера отчетов (ReportServer, ReportServerTempdb). Можно также создать роль RSExecRole в системной базе данных Master, когда производится перемещение базы данных сервера отчетов на новое или другое ядро СУБД (компонент[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]). Дополнительные сведения об этих задачах см. в следующих разделах:  
  
-   [Службы Reporting Services в среде SQL Server Management Studio (SSRS)](../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
-   [Администрирование служб SSRS базы данных &#40;сервера отчетов в собственном режиме&#41;](../reporting-services/report-server/report-server-database-ssrs-native-mode.md)  
  
-   [Создание роли RSExecRole](../reporting-services/security/create-the-rsexecrole.md)  
  
 Позволяет включать и настраивать различные функции, задавать для сервера значения по умолчанию, управлять ролями и заданиями. Дополнительные сведения об этих задачах см. в следующих разделах:  
  
-   [Установка свойств сервера отчетов (среда Management Studio)](../reporting-services/tools/set-report-server-properties-management-studio.md)  
  
-   [Создание, удаление и изменение ролей (среда Management Studio)](../reporting-services/security/role-definitions-create-delete-or-modify.md)  
  
-   [Включение и отключение печати на стороне клиента для служб Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)  
  
## <a name="see-also"></a>См. также  
 [Создание многомерных моделей с помощью SQL Server Data Tools (SSDT)](https://docs.microsoft.com/analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt)   
 [Reporting Services в SQL Server Data Tools &#40;SSDT&#41;](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)  
  
  
