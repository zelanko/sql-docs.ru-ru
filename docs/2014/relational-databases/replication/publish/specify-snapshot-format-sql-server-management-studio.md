---
title: Указание формата моментальных снимков (SQL Server Management Studio) | Документация Майкрософт
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
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b5ce1a19139ab8a399cd223e77d24cd135e225a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250024"
---
# <a name="specify-snapshot-format-sql-server-management-studio"></a>указать формат моментальных снимков (среда SQL Server Management Studio)
  Укажите формат моментального снимка на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>Указание формата моментальных снимков  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** выберите вариант **Собственный SQL Server — все подписчики должны быть серверами SQL Server** или **Символьный — необходим в том случае, если на стороне издателя или подписчика не используется SQL Server**.  
  
    > [!NOTE]  
    >  Рекомендуется выбирать собственный формат всегда, кроме тех случаев, когда публикация должна поддерживать подписки на базу данных [!INCLUDE[ssEW](../../../includes/ssew-md.md)] или базу данных, отличную от базы данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../initialize-a-subscription-with-a-snapshot.md)  
  
  
