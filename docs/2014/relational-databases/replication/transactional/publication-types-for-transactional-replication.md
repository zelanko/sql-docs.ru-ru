---
title: Типы публикации для репликации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 88941deda14053fdf2eac1e1600b4ef02253b401
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181901"
---
# <a name="publication-types-for-transactional-replication"></a>Типы публикации для репликации транзакций
  Репликации транзакций поддерживают три типа публикаций:  
  
|Тип публикации|Описание|  
|----------------------|-----------------|  
|Стандартная публикация транзакций|Подходит для топологий, в которых все данные подписчика доступны только для чтения (репликация транзакций не устанавливает принудительно этот вид доступа на подписчике).<br /><br /> Стандартные публикации транзакций создаются по умолчанию, если используется Transact-SQL или объекты RMO. Если используется мастер создания публикации, публикации транзакций создаются путем выбора **Публикация транзакций** на странице **Тип публикации** .<br /><br /> Дополнительные сведения о создании публикаций см. в статье [Публикация данных и объектов базы данных](../publish/publish-data-and-database-objects.md).|  
|Публикации транзакций в одноранговой топологии|Ниже приведены характеристики этого типа публикации:<br /><br /> Каждое расположение содержит идентичные данные и действует и как издатель, и как подписчик.<br /><br /> Одна и та же строка может быть изменена за раз только в одном расположении.<br /><br /> Эта топология более всего подходит для серверных сред, в которых требуется высокий уровень масштабируемости доступности и чтения.<br /><br /> <br /><br /> Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>См. также  
 [Репликация транзакций](transactional-replication.md)  
  
  
