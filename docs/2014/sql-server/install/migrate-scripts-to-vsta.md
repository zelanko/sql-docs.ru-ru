---
title: Миграция скриптов в VSTA | Документы Microsoft
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
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
caps.latest.revision: 44
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 99acbad66d2a614431bc1f08ad88bd12f2a3e6b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194416"
---
# <a name="migrate-scripts-to-vsta"></a>Миграция скриптов в VSTA
  При обновлении [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пакетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переносит скрипты в задачах «скрипт» и компонентов скрипта в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средств для приложений (VSTA). VSTA — среда выполнения сценариев, используемая службами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], среда скриптов для [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSA).  
  
 Если скрипты в задачах или компонентах скрипта содержат ссылки на интерфейсы, то перед обновлением пакета эти ссылки, возможно, придется изменить. В противном случае в зависимости от используемого метода обновления либо пакет не будет обновлен, либо не удастся подтвердить правильность скриптов. Чтобы изменить эти ссылки, замените ссылки на IDTS*xxx*90 интерфейсы со ссылками на соответствующие IDTS*xxx*100 интерфейсов.  
  
 Дополнительные сведения о переносе скриптов и пакетов обновления см. в разделе [обновление пакетов служб Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Основные сведения об ошибках миграции  
 При переносе скриптов миграция может завершиться ошибкой по одной из следующих причин.  
  
-   Точка входа для скрипта VSA была переименована.  
  
     Точка входа указывает метод класса `ScriptMain` в проекте VSTA, который службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вызывают во время выполнения как точку входа в код задачи «Скрипт». Класс `ScriptMain` является классом по умолчанию, создаваемым шаблонами скриптов.  
  
-   Не существует точки входа, или имеется несколько точек входа в скрипты VSA.  
  
-   Не удалось добавить ссылки на сборку.  
  
-   Класс `ScriptMain` был изменен. В него была добавлена возможность наследования из других классов в дополнение к классу `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] не поддерживает множественное наследование.  
  
 Не удается преобразовать скрипт VSA, использующий [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] в скрипт VSTA, использующий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Тем не менее, можно создать новый скрипт VSTA, использующий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Дополнительные сведения см. в разделах [Кодирование и отладка задачи "Скрипт"](../../integration-services/control-flow/script-task.md) и [Кодирование и отладка компонента скрипта](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  