---
title: Указание формата моментальных снимков (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5bf7b52c915d8ca61338c7724ab3c2f757f358a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601292"
---
# <a name="specify-snapshot-format-sql-server-management-studio"></a>указать формат моментальных снимков (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Укажите формат моментального снимка на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>Указание формата моментальных снимков  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** выберите вариант **Собственный SQL Server — все подписчики должны быть серверами SQL Server** или **Символьный — необходим в том случае, если на стороне издателя или подписчика не используется SQL Server**.  
  
    > [!NOTE]  
    >  Рекомендуется выбирать собственный формат всегда, кроме тех случаев, когда публикация должна поддерживать подписки на базу данных [!INCLUDE[ssEW](../../../includes/ssew-md.md)] или базу данных, отличную от базы данных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
