---
title: "Публикация выполнения хранимой процедуры в публикации транзакций | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3cd29554f7301368b8e58e47e73622365d5f273c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Публикация выполнения хранимой процедуры в публикации транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В диалоговом окне **Свойства статьи — \<статья>** можно указать, что публикуется не только определение, но и выполнение хранимой процедуры. Это диалоговое окно доступно в мастере создания публикаций, а также в диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера создания публикаций и доступе к этому диалоговому окну см. в статьях о [создании публикаций](../../../relational-databases/replication/publish/create-a-publication.md) и [просмотре и изменении свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Определение процедуры (инструкция CREATE PROCEDURE) реплицируется на подписчик при инициализации подписки. Когда процедура выполняется на издателе, репликация выполняет соответствующую процедуру на подписчике.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Публикация выполнения хранимой процедуры  
  
1.  Выберите хранимую процедуру на странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>**.  
  
2.  Щелкните **Свойства статьи**, а затем щелкните **Задать свойства выделенной хранимой процедуры**.  
  
3.  В диалоговом окне **Свойства статьи — \<статья>** укажите одно из следующих значений для параметра **Репликация**.  
  
    -   **Выполнение хранимой процедуры**  
  
    -   **Выполнение в сериализованной транзакции хранимой процедуры**  
  
         Это рекомендуемый параметр, поскольку он реплицирует выполнение процедуры только в случае ее выполнения в контексте сериализуемой транзакции. При выполнении хранимой процедуры вне сериализуемой транзакции изменения, вносимые в данные опубликованных таблиц, реплицируются как ряды инструкций языка обработки данных.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
## <a name="see-also"></a>См. также:  
 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
