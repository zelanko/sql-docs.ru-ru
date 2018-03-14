---
title: "Типы публикации для репликации транзакций | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d2ce9609cb89baf0418449e2fd1b4d9bf1cd94c9
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="publication-types-for-transactional-replication"></a>Типы публикации для репликации транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Репликации транзакций поддерживают три типа публикаций:  
  
|Тип публикации|Description|  
|----------------------|-----------------|  
|Стандартная публикация транзакций|Подходит для топологий, в которых все данные подписчика доступны только для чтения (репликация транзакций не устанавливает принудительно этот вид доступа на подписчике).<br /><br /> Стандартные публикации транзакций создаются по умолчанию, если используется Transact-SQL или объекты RMO. Если используется мастер создания публикации, публикации транзакций создаются путем выбора **Публикация транзакций** на странице **Тип публикации** .<br /><br /> Дополнительные сведения о создании публикаций см. в статье [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).|  
|Публикации транзакций в одноранговой топологии|Ниже приведены характеристики этого типа публикации:<br /><br /> -Каждое расположение содержит идентичные данные и действует и как издатель, и как подписчик.<br /><br /> -Одна и та же строка может быть изменена за раз только в одном расположении.<br /><br /> -Эта топология более всего подходит для серверных сред, в которых требуется высокий уровень масштабируемости доступности и чтения.<br /><br /> <br /><br /> Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>См. также:  
 [Репликация транзакций](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
