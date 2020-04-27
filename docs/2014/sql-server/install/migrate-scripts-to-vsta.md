---
title: Перенос скриптов в VSTA | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: cb44a7b635e24c0c2e3266c1cca98a9c4f6a347c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093989"
---
# <a name="migrate-scripts-to-vsta"></a>Миграция скриптов в VSTA
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] При обновлении [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]пакетов до [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переносит скрипты в любой задаче или компонентах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] скриптов в средства для приложений (VSTA). VSTA — среда выполнения сценариев, используемая службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]среде Среда скриптов для [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предназначена [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSA).  
  
 Если скрипты в задачах или компонентах скрипта содержат ссылки на интерфейсы, то перед обновлением пакета эти ссылки, возможно, придется изменить. В противном случае в зависимости от используемого метода обновления либо пакет не будет обновлен, либо не удастся подтвердить правильность скриптов. Чтобы изменить эти ссылки, замените ссылки на интерфейсы IDTS*xxx*90 ссылками на соответствующие интерфейсы IDTS*xxx*100.  
  
 Дополнительные сведения о переносе скриптов и обновлении пакетов см. в разделе [upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Основные сведения об ошибках миграции  
 При переносе скриптов миграция может завершиться ошибкой по одной из следующих причин.  
  
-   Точка входа для скрипта VSA была переименована.  
  
     Точка входа указывает метод класса `ScriptMain` в проекте VSTA, который службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вызывают во время выполнения как точку входа в код задачи «Скрипт». Класс `ScriptMain` является классом по умолчанию, создаваемым шаблонами скриптов.  
  
-   Не существует точки входа, или имеется несколько точек входа в скрипты VSA.  
  
-   Не удалось добавить ссылки на сборку.  
  
-   Класс `ScriptMain` был изменен. В него была добавлена возможность наследования из других классов в дополнение к классу `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] не поддерживает множественное наследование.  
  
 Невозможно преобразовать скрипт VSA, который использует [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] , в скрипт VSTA, использующий. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] Однако можно создать новый скрипт VSTA, использующий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Дополнительные сведения см. в разделах [Кодирование и отладка задачи "Скрипт"](../../integration-services/control-flow/script-task.md) и [Кодирование и отладка компонента скрипта](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
