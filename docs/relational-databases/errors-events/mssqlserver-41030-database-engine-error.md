---
description: MSSQLSERVER_41030
title: MSSQLSERVER_41030 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1420fb5c7abac41430135cec85c4e15e2737cc46
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471107"
---
# <a name="mssqlserver_41030"></a>MSSQLSERVER_41030
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
