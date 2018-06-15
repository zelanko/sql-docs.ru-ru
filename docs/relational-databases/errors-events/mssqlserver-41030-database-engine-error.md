---
title: MSSQLSERVER_41030 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d7fac53bcfbd33b2a12499529f00dbb99685a6d6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321955"
---
# <a name="mssqlserver41030"></a>MSSQLSERVER_41030
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41030|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|OPEN_CLUSTER_SUB_KEY|  
|Текст сообщения|Не удалось открыть подраздел реестра отказоустойчивой кластеризации Windows Server «%.*ls» (код ошибки: %d).  Родительский ключ — это корневой ключ кластера.  Возможно, что служба WSFC не работает или недоступна в текущем состоянии либо указанные аргументы недопустимы. Если соответствующие группы доступности удалены, это ожидаемая ошибка. Дополнительные сведения о коде ошибки см. в разделе «Системные коды ошибок» в документации по разработке для Windows.|  
  
## <a name="explanation"></a>Объяснение  
Если кластер WSFC разрушается, удаляются все разделы реестра, связанные с [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
## <a name="user-action"></a>Действие пользователя  
После повторного создания кластера WSFC необходимо отключить и повторно включить группы доступности AlwaysOn на каждом узле кластера, на котором для AlwaysOn включен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для этой задачи вы можете использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
[Включение и отключение групп доступности AlwaysOn (SQL Server)](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
[Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](~/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
