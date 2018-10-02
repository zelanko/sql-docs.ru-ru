---
title: Добавление и удаление статей в существующих публикациях | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8382624490df51ce0c44856363247697a546a9b1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634362"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication"></a>Добавление и удаление статей в существующих публикациях
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Вначале статьи в публикацию добавляются при ее создании в мастере создания публикации. Дополнительные сведения об использовании мастера см. в статье [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 После создания публикации вы можете добавлять и удалять статьи на странице **Статьи** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). Сведения о добавлении и удалении статей см. в статье [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
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
  
  
