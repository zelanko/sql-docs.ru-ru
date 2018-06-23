---
title: Взаимодействие и совместная работа (службы Integration Services) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d0db34c7b894dc7b92ad6061d4f3c53c1cd2dbe9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095246"
---
# <a name="interoperability-and-coexistence-integration-services"></a>Функциональная совместимость и параллельная работа (службы Integration Services)
  Службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) могут работать совместно со службами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services.  
  
## <a name="features-and-differences"></a>Функции и отличия  
 В следующей таблице приводятся некоторые отличия между текущей и более ранними версиями служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Компонент|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|Среда разработки|[SQL Server 2014 Data Tools — бизнес-аналитика для Visual Studio 2012 CTP 2](http://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools - Business Intelligence для Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=42313)|[SQL Server Data Tools для Visual Studio 2010](http://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools — бизнес-аналитика для Visual Studio 2012](http://www.microsoft.com/download/details.aspx?id=36843)|Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|Среда управления|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|Основная системная таблица в базе данных msdb для хранения пакетов|sysssispackages|sysssispackages|sysssispackages|  
|Основная программа командной строки для запуска пакетов|**dtexec** (dtexec.exe), версия 2014|**dtexec** (dtexec.exe), версия 2012|**dtexec** (dtexec.exe), версия 2008|  
|Корневая папка файловой системы по умолчанию|C:\Program Files\Microsoft SQL Server\120\DTS|C:\Program Files\Microsoft SQL Server\110\DTS|C:\Program Files\Microsoft SQL Server\100\DTS|  
|Корневой раздел реестра по умолчанию|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>Вопросы совместимости параллельной установки  
 Если службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services установлены параллельно со службами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services, можно выполнять следующие задачи.  
  
-   **Проектирование пакетов в SQL Server Data Tools**. Для разработки и обслуживания пакетов, основанных на соответствующих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используются следующие средства.  
  
    -   Для разработки и обслуживания пакетов на основе служб [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] используйте среду Business Intelligence Development Studio версии [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
    -   Используйте [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для разработки и обслуживания пакетов на основе [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
    -   Используйте [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для разработки и обслуживания пакетов на основе [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   **Разработка и запуск пакетов**; Можно загружать и запускать пакеты, разработанные в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Пакет, добавленный в существующий проект, окончательно обновляется до формата, используемого службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. Пакет, открытый в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], временно обновляется до формата, используемого службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. В случае сохранения пакета обновление пакета станет необратимым. После сохранения в формате, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] использует службы Integration Services, пакетов, больше нельзя открывать в соответствующей [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии Business Intelligence Development Studio, а также запускать с помощью соответствующих [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Службы Integration Services или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] служб Integration Services.  
  
-   **Управление пакетами в среде SQL Server Management Studio**. Не удается подключиться к экземпляру компонента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] службой [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Не удается подключиться к экземпляру компонента [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Среду [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] можно использовать для управления пакетами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], хранящимися в экземпляре [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Необходимо внести изменения в файл конфигурации службы, добавив экземпляр [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] в список расположений, управляемых службой. Дополнительные сведения см. в разделе [Configuring the Integration Services Service &#40;SSIS Service&#41;](../service/integration-services-service-ssis-service.md).  
  
-   **Хранить пакеты в SQL Server**. Пакеты можно сохранять в следующих базах данных.  
  
    |Формат пакета|База данных|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Службы Integration Services|База данных msdb экземпляра [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Службы Integration Services|База данных msdb экземпляра [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Службы Integration Services|База данных msdb экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     На экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], можно импортировать пакеты из экземпляра [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или из экземпляра [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], но нельзя экспортировать пакеты в экземпляре [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или к экземпляру компонента [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
     В экземпляре [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] нельзя ни импортировать пакеты из экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ни экспортировать пакеты в него.  
  
-   **Запускать пакеты**. Можно запустить [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] служб Integration Services и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] пакетов служб Integration Services с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] версии **dtexec** программы или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Каждый раз, когда [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] средство служб Integration Services загружает пакет, разработанный в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], оно временно преобразует в памяти, пакет в формат, [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] использует. Если [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] пакет вызывает проблемы, препятствующие успешному преобразованию, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] программы служб интеграции не удается запустить пакет, пока проблемы не будут устранены. Дополнительные сведения см. в разделе [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).  
  
  