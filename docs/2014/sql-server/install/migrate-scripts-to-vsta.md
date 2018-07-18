---
title: Миграция скриптов в VSTA | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
caps.latest.revision: 44
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 87c4c76ef7a09b8c03d0c95f83b647b73ccb3325
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157525"
---
# <a name="migrate-scripts-to-vsta"></a>Миграция скриптов в VSTA
  При обновлении [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переносит скрипт в любой задачи или компонентов скрипта в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). VSTA — среда выполнения сценариев, используемая службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], среда разработки скриптов для [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSA).  
  
 Если скрипты в задачах или компонентах скрипта содержат ссылки на интерфейсы, то перед обновлением пакета эти ссылки, возможно, придется изменить. В противном случае в зависимости от используемого метода обновления либо пакет не будет обновлен, либо не удастся подтвердить правильность скриптов. Чтобы изменить эти ссылки, замените ссылки на IDTS*xxx*90 интерфейсы со ссылками на соответствующие IDTS*xxx*100 интерфейсов.  
  
 Дополнительные сведения о переносе скриптов и обновить пакеты, см. в разделе [обновление пакетов служб Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Основные сведения об ошибках миграции  
 При переносе скриптов миграция может завершиться ошибкой по одной из следующих причин.  
  
-   Точка входа для скрипта VSA была переименована.  
  
     Точка входа указывает метод класса `ScriptMain` в проекте VSTA, который службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вызывают во время выполнения как точку входа в код задачи «Скрипт». Класс `ScriptMain` является классом по умолчанию, создаваемым шаблонами скриптов.  
  
-   Не существует точки входа, или имеется несколько точек входа в скрипты VSA.  
  
-   Не удалось добавить ссылки на сборку.  
  
-   Класс `ScriptMain` был изменен. В него была добавлена возможность наследования из других классов в дополнение к классу `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] не поддерживает множественное наследование.  
  
 Не удается преобразовать скрипт VSA, который использует [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] в скрипт VSTA, который использует [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Тем не менее, можно создать новый скрипт VSTA, использующий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Дополнительные сведения см. в разделах [Кодирование и отладка задачи "Скрипт"](../../integration-services/control-flow/script-task.md) и [Кодирование и отладка компонента скрипта](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
