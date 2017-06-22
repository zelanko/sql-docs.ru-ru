---
title: "Введение в среду SQL Server Management Studio для решения задач бизнес-аналитики | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.assetid: ffaa77b7-03d0-4d7a-aa42-c5091a4f2ceb
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a94d889f59d03adf7ece002e02e54f56704d437c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="introduction-to-sql-server-management-studio-for-business-intelligence"></a>Введение в среду SQL Server Management Studio для решения задач бизнес-аналитики
Среда [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] предназначена для доступа к службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)] и [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], а также для их настройки, администрирования и управления ими. Хотя все три технологии бизнес-аналитики полагаются на среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], административные задачи, связанные с каждой из этих технологий, несколько отличаются.  
  
> [!NOTE]  
> Чтобы создать и изменить решения [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)]и [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] , воспользуйтесь [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)], а не [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)] представляет собой среду разработки, основанную на [!INCLUDE[msCoName](../includes/msconame_md.md)][!INCLUDE[vsprvs](../includes/vsprvs_md.md)].  
  
## <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Управление решениями Analysis Services в среде SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] позволяет управлять объектами служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] , например выполнять их резервное копирование и обработку.  
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] позволяет создавать проекты скриптов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] , в которых выполняются разработка и сохранение скриптов с использованием многомерных выражений (MDX), расширений интеллектуального анализа данных (DMX) и XML для аналитики (XMLA). Проекты скриптов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] используются для выполнения задач управления или повторного создания баз данных, кубов и других объектов в экземплярах служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] . Например, можно разработать скрипт XMLA в проекте скрипта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] , который создает объекты непосредственно в существующем экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] . Проекты скриптов служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] могут быть сохранены в составе решения и интегрироваться с контролем исходного кода.  
  
Дополнительные сведения об использовании среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]см. в разделе [Разработка и реализация с помощью среды SQL Server Management Studio](http://msdn.microsoft.com/en-us/c4f5a06b-e2e4-4660-a3a8-6fd356742c02).  
  
## <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Управление решениями Integration Services в среде SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] позволяет использовать службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] для управления пакетами и наблюдения за выполняющимися пакетами. В среде [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] можно организовать пакеты в папки, выполнять, импортировать и экспортировать пакеты, переносить пакеты служб DTS и обновлять пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion_md.md)] .  
  
## <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Управление проектами служб Reporting Service в среде SQL Server Management Studio  
Среда SQL Server Management Studio позволяет включать компоненты служб Reporting Services, администрировать серверы и базы данных, управлять ролями и заданиями.  
  
Она реализует функции управления общими расписаниями (в папке «Общие расписания») и базами данных сервера отчетов (ReportServer, ReportServerTempdb). Можно также создать роль RSExecRole в системной базе данных Master, когда производится перемещение базы данных сервера отчетов на новое или другое ядро СУБД (компонент[!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] [!INCLUDE[ssDE](../includes/ssde_md.md)]). Дополнительные сведения об этих задачах см. в следующих разделах:  
  
-   [Разделы руководства по использованию среды Management Studio](http://msdn.microsoft.com/en-us/60685458-9108-47bf-820a-5e7db454d408)  
  
-   [Администрирование баз данных сервера отчетов](http://msdn.microsoft.com/en-us/97b2e1b5-3869-4766-97b9-9bf206b52262)  
  
-   [Практическое руководство. Создание роли RSExecRole](http://msdn.microsoft.com/en-us/7ac17341-df7e-4401-870e-652caa2859c0)  
  
Позволяет включать и настраивать различные функции, задавать для сервера значения по умолчанию, управлять ролями и заданиями. Дополнительные сведения об этих задачах см. в следующих разделах:  
  
-   [Практическое руководство. Установка свойств сервера отчетов (среда Management Studio)](http://msdn.microsoft.com/en-us/1ed0f84b-b12a-4e49-b65c-a11a99f9093f)  
  
-   [Практическое руководство. Создание, удаление и изменение ролей (среда Management Studio)](http://msdn.microsoft.com/en-us/3d1d56e6-a283-44a7-8417-36cb4d2c74d1)  
  
-   [Разрешение и запрет печати на стороне клиента для служб Reporting Services](http://msdn.microsoft.com/en-us/0e709c96-7517-4547-8ef6-5632f8118524)  
  
## <a name="see-also"></a>См. также:  
[Разработка и реализация с помощью SQL Server Data Tools](http://msdn.microsoft.com/en-us/132ed779-3ec8-4734-9698-802116d1b017)  
[Службы Reporting Services в SQL Server Data Tools](http://msdn.microsoft.com/en-us/0903c7b2-ac59-45f1-b7d0-922ecd9d76f8)  
  

