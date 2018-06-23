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
ms.topic: article
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 11e9e6ffafe62c66684470b4b04e2e0b67cc868b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095649"
---
# <a name="publication-types-for-transactional-replication"></a>Типы публикации для репликации транзакций
  Репликации транзакций поддерживают три типа публикаций:  
  
|Тип публикации|Описание|  
|----------------------|-----------------|  
|Стандартная публикация транзакций|Подходит для топологий, в которых все данные подписчика доступны только для чтения (репликация транзакций не устанавливает принудительно этот вид доступа на подписчике).<br /><br /> Стандартные публикации транзакций создаются по умолчанию, если используется Transact-SQL или объекты RMO. Если используется мастер создания публикации, публикации транзакций создаются путем выбора **Публикация транзакций** на странице **Тип публикации** .<br /><br /> Дополнительные сведения о создании публикаций см. в статье [Публикация данных и объектов базы данных](../publish/publish-data-and-database-objects.md).|  
|Публикации транзакций в одноранговой топологии|Ниже приведены характеристики этого типа публикации:<br /><br /> Каждое расположение содержит идентичные данные и действует и как издатель, и как подписчик.<br /><br /> Одна и та же строка может быть изменена за раз только в одном расположении.<br /><br /> Эта топология более всего подходит для серверных сред, в которых требуется высокий уровень масштабируемости доступности и чтения.<br /><br /> <br /><br /> Дополнительные сведения см. в разделе [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>См. также  
 [Репликация транзакций](transactional-replication.md)  
  
  