---
title: "Типы подписчиков | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ae9c8cf11d6a95554f56d6c6bde1b2eb18b36d70
ms.lasthandoff: 04/11/2017

---
# <a name="subscriber-types"></a>Типы подписчиков
  Репликация слиянием позволяет задавать типы подписчиков, которые должна поддерживать публикация. Выбор типов подписчиков устанавливает *уровень совместимости публикации*, который определяет, какие возможности будут использоваться публикацией.  
  
 После создания моментального снимка публикации можно повысить ее уровень совместимости (еще более ограничить ее совместимость) на странице **Общие** диалогового окна **Свойства публикации** . Понизить уровень совместимости нельзя.  
  
## <a name="options"></a>Параметры  
 Выберите тип подписчика, который должна поддерживать эта публикация.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Публикация может использовать все возможности.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 Публикации требуется, чтобы файлы моментального снимка имели символьный формат (агент моментальных снимков выполняет это автоматически). [!INCLUDE[ssEW](../../includes/ssew-md.md)] также имеет ряд ограничений, не связанных с уровнем совместимости.  
  
 Если выбран этот параметр, то для публикации включается параметр веб-синхронизации. Дополнительные сведения о веб-синхронизации см. в разделе [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам (репликация)](../../relational-databases/replication/properties-reference-replication.md)  
  
  
