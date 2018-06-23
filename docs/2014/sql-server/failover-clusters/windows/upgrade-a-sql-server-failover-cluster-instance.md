---
title: Обновление отказоустойчивого кластера SQL Server | Документы Microsoft
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
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 80f961a228d96561c79fa065b557e229517f73ee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192370"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a>Обновление отказоустойчивого кластера SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает отдельное обновление компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] и служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с версий [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] и [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] отказоустойчивого кластера на всех узлах отказоустойчивого кластера.  
  
 Далее приведены сведения о поддержке:  
  
-   Обновление поддерживается как через пользовательский интерфейс, так и из командной строки. Дополнительные сведения см. в статьях [Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](upgrade-a-sql-server-failover-cluster-instance-setup.md) и [Установка SQL Server 2014 из командной строки](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
-   Обновление с версии [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] — обновление можно запустить из командной строки на каждом узле отказоустойчивого кластера, либо каждый узел кластера можно обновить при помощи пользовательского интерфейса программы установки. Если компоненты Full-Text Search и репликации не существуют на обновляемом экземпляре, они будут установлены автоматически, при этом возможности отключить их установку нет.  
  
-   Установка пакета обновления — на отказоустойчивых кластерах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] пакеты обновления и обновления [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] следует устанавливать для каждого узла отдельно.  
  
-   Следующие сценарии не поддерживаются.  
  
    -   Невозможно перенести изолированный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на кластер отработки отказа.  
  
    -   Добавление компонентов в кластер отработки отказа. Например, невозможно добавить компонент [!INCLUDE[ssDE](../../../includes/ssde-md.md)] в существующий отказоустойчивый кластер, имеющий только службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
    -   Невозможно понизить узел отказоустойчивого кластера до изолированного экземпляра.  
  
-   Дополнительные сведения см. в разделе [ экземпляры отказоустойчивого кластера AlwaysOn (SQL Server)](always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="upgrading-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>Обновление отказоустойчивого кластера с несколькими подсетями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 Обновить отказоустойчивый кластер с одной подсетью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] до отказоустойчивого кластера с несколькими подсетями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] напрямую нельзя. Дополнительные сведения см. на разделе [Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](upgrade-a-sql-server-failover-cluster-instance-setup.md).  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые обновления версий и выпусков](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Обновление экземпляра отказоустойчивого кластера SQL Server &#40;установки&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)   
 [Установка SQL Server 2014 из командной строки](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  