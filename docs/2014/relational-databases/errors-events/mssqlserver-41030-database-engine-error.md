---
title: MSSQLSERVER_41030 | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 135b177d181556dae733ffc352122435f51bc5a0
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551519"
---
# <a name="mssqlserver_41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
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
 [Включение и отключение группы доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
