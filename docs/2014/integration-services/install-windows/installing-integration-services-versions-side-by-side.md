---
title: Взаимодействие и совместная работа (службы Integration Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5552780cdc4a2f4e3faf39b9111882fcf4ffdd63
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58380122"
---
# <a name="interoperability-and-coexistence-integration-services"></a>Функциональная совместимость и параллельная работа (службы Integration Services)
  Службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) могут работать совместно со службами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services.  
  
## <a name="features-and-differences"></a>Функции и отличия  
 В следующей таблице приводятся некоторые отличия между текущей и более ранними версиями служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Компонент|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|Среда разработки|[SQL Server 2014 Data Tools - Business Intelligence для Visual Studio 2012 CTP 2](https://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools - Business Intelligence для Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=42313)|[SQL Server Data Tools для Visual Studio 2010](https://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools - Business Intelligence для Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843)|Среда Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|Среда управления|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|Основная системная таблица в базе данных msdb для хранения пакетов|sysssispackages|sysssispackages|sysssispackages|  
|Основная программа командной строки для запуска пакетов|**dtexec** (dtexec.exe), версия 2014|**dtexec** (dtexec.exe), версия 2012|**dtexec** (dtexec.exe), версия 2008|  
|Корневая папка файловой системы по умолчанию|C:\Program Files\Microsoft SQL Server\120\DTS|C:\Program Files\Microsoft SQL Server\110\DTS|C:\Program Files\Microsoft SQL Server\100\DTS|  
|Корневой раздел реестра по умолчанию|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>Вопросы совместимости параллельной установки  
 Если службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services установлены параллельно со службами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services, можно выполнять следующие задачи.  
  
-   **Проектирование пакетов в SQL Server Data Tools**. Для разработки и обслуживания пакетов, основанных на соответствующих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используются следующие средства.  
  
    -   Для разработки и обслуживания пакетов на основе служб [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] используйте среду Business Intelligence Development Studio версии [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
    -   Для разработки и обслуживания пакетов на основе служб [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] используйте среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] версии [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
    -   Для разработки и обслуживания пакетов на основе служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] используйте среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] версии [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   **Разработка и запуск пакетов**; В среде [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]можно загружать и выполнять пакеты, созданные в службах [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Пакет, добавленный в существующий проект, окончательно обновляется до формата, используемого службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. Пакет, открытый в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], временно обновляется до формата, используемого службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. В случае сохранения пакета обновление пакета станет необратимым. После сохранения в формате, используемом службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services, пакеты больше нельзя открывать в соответствующей версии Business Intelligence Development Studio для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и запускать с помощью соответствующих средств служб [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services.  
  
-   **Управление пакетами в среде SQL Server Management Studio**. Из среды [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] нельзя соединиться со службой [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Из среды [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] нельзя соединиться с экземпляром служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Среду [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] можно использовать для управления пакетами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , хранящимися в экземпляре [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Необходимо внести изменения в файл конфигурации службы, добавив экземпляр [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] в список расположений, управляемых службой. Дополнительные сведения см. в разделе [Настройка служб Integration Services (службы SSIS)](../service/integration-services-service-ssis-service.md).  
  
-   **Хранить пакеты в SQL Server**. Пакеты можно сохранять в следующих базах данных.  
  
    |Формат пакета|База данных|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Службы Integration Services|База данных msdb экземпляра [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Службы Integration Services|База данных msdb экземпляра [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Службы Integration Services|База данных msdb экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     В экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]можно импортировать пакеты из экземпляра [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или экземпляра [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], но экспорт пакетов в экземпляр [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]невозможен.  
  
     В экземпляре [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]нельзя ни импортировать пакеты из экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ни экспортировать пакеты в него.  
  
-   **Запускать пакеты**. Пакеты служб [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services можно запускать с помощью служебной программы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии **dtexec** или агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] той же версии. Каждый раз, когда средство служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services загружает пакет, разработанный в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], оно временно в памяти преобразует пакет в формат пакета, используемый [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] . Если пакет [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] связан с проблемами, приводящими к невозможности преобразования, средство служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services сможет запускать пакет только после устранения этих проблем. Дополнительные сведения см. в разделе [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).  
  
  
