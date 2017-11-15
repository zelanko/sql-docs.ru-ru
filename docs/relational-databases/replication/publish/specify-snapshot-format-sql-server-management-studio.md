---
title: "Указание формата моментальных снимков (SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
caps.latest.revision: "38"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2d9b8617b69eeba253639bff5190c1cc5453788
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="specify-snapshot-format-sql-server-management-studio"></a>указать формат моментальных снимков (среда SQL Server Management Studio)
  Укажите формат моментального снимка на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>Указание формата моментальных снимков  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** выберите вариант **Собственный SQL Server — все подписчики должны быть серверами SQL Server** или **Символьный — необходим в том случае, если на стороне издателя или подписчика не используется SQL Server**.  
  
    > [!NOTE]  
    >  Рекомендуется выбирать собственный формат всегда, кроме тех случаев, когда публикация должна поддерживать подписки на базу данных [!INCLUDE[ssEW](../../../includes/ssew-md.md)] или базу данных, отличную от базы данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
