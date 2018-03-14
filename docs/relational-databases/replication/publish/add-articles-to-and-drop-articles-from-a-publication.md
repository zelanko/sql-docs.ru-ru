---
title: "Добавление и удаление статей в существующих публикациях | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
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
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 916988523200384f9d7b792147e61e7926826f60
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="add-articles-to-and-drop-articles-from-a-publication"></a>Добавление и удаление статей в существующих публикациях
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Вначале статьи в публикацию добавляются при ее создании в мастере создания публикации. Дополнительные сведения об использовании мастера см. в статье [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 После создания публикации вы можете добавлять и удалять статьи на странице **Статьи** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Сведения о добавлении и удалении статей см. в статье [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a>Добавление статьи после создания публикации  
  
1.  На странице **Статьи** диалогового окна **Свойства публикации — \<публикация>** снимите флажок **Показывать в списке только отмеченные объекты**. Это позволит увидеть неопубликованные объекты в базе данных публикаций.  
  
2.  Установите флажок рядом с каждой статьей, которую нужно добавить.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a>Удаление статьи  
  
1.  На странице **Статьи** диалогового окна **Свойства публикации — \<название публикации>** снимите флажки напротив всех статей, которые нужно удалить.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Определение статьи](../../../relational-databases/replication/publish/define-an-article.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
