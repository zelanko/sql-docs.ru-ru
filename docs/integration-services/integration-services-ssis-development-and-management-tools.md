---
title: Средства разработки и управления Integration Services (SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3c37cdf1866a10f538baaa7b6536e74c88225de8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65723588"
---
# <a name="integration-services-ssis-development-and-management-tools"></a>Средства разработки и управления Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержат две интегрированные среды для работы с пакетами:  
  
-   Среда[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предназначена для разработки пакетов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , необходимых для бизнес-решения. Среда[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] предоставляет проект [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в котором можно создавать пакеты.  
  
-   Среда[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] предназначена для управления пакетами в рабочей среде.  
  
## <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 Работая в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], можно выполнять следующие задачи:  
  
-   Запускать мастер импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для создания основных пакетов, которые осуществляют копирование данных из источника в место назначения.  
  
-   Создавать пакеты, содержащие сложные потоки управления, потоки данных, событийно-управляемую логику и ведение журнала.  
  
-   Проверять и запускать отладку для пакетов при помощи функций диагностики и наблюдения в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и функций отладки в [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   Создавать настройки для обновления свойств пакетов и объектов пакетов в процессе выполнения.  
  
-   Создавать программу развертывания, при помощи которой можно устанавливать пакеты и их зависимости на другие компьютеры.  
  
-   Сохранять копии пакетов в базе данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb, в хранилище пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и в файловой системе.  
  
 Дополнительные сведения о [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]см. в разделе [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/hh272686.aspx).  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Среда[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] предоставляет службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , применяемую для управления пакетами и контроля за выполнением пакетов, а также для определения влияния и преобразования данных для объектов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Работая в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], можно выполнять следующие задачи:  
  
-   Создавать папки для систематизации пакетов нужным для организации образом.  
  
-   Запускать пакеты, хранимые на локальном компьютере, при помощи программы выполнения пакетов.  
  
-   Запустите программу выполнения пакетов для создания командной строки, которую можно использовать в программе командной строки **dtexec** (dtexec.exe).  
  
-   Проводить операции импорта и экспорта пакетов с базой данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb, хранилищами пакетов [!INCLUDE[ssIS](../includes/ssis-md.md)] и с файловой системой.  
