---
description: Типы подписчиков
title: Типы подписчиков | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016
ms.openlocfilehash: 0f6ba4369e2ac2da9058621108f310e1b3f8e953
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97480965"
---
# <a name="subscriber-types"></a>Типы подписчиков
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Репликация слиянием позволяет задавать типы подписчиков, которые должна поддерживать публикация. Выбор типов подписчиков устанавливает *уровень совместимости публикации*, который определяет, какие возможности будут использоваться публикацией.  
  
 После создания моментального снимка публикации можно повысить ее уровень совместимости (еще более ограничить ее совместимость) на странице **Общие** диалогового окна **Свойства публикации** . Понизить уровень совместимости нельзя.  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Варианты  
 Выберите тип подписчика, который должна поддерживать эта публикация.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Публикация может использовать все возможности.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 Публикации требуется, чтобы файлы моментального снимка имели символьный формат (агент моментальных снимков выполняет это автоматически). [!INCLUDE[ssEW](../../includes/ssew-md.md)] также имеет ряд ограничений, не связанных с уровнем совместимости.  
  
 Если выбран этот параметр, то для публикации включается параметр веб-синхронизации. Дополнительные сведения о веб-синхронизации см. в разделе [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
  
  
