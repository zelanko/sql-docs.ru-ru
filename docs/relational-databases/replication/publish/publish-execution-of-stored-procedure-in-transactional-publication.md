---
title: Публикация выполнения хранимой процедуры в публикации транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 122be6c923d45a0ba0416f114c58c762faff9c35
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Публикация выполнения хранимой процедуры в публикации транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В диалоговом окне **Свойства статьи — \<статья>** можно указать, что публикуется не только определение, но и выполнение хранимой процедуры. Это диалоговое окно доступно в мастере создания публикаций, а также в диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Определение процедуры (инструкция CREATE PROCEDURE) реплицируется на подписчик при инициализации подписки. Когда процедура выполняется на издателе, репликация выполняет соответствующую процедуру на подписчике.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Публикация выполнения хранимой процедуры  
  
1.  Выберите хранимую процедуру на странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>**.  
  
2.  Щелкните **Свойства статьи**, а затем щелкните **Задать свойства выделенной хранимой процедуры**.  
  
3.  В диалоговом окне **Свойства статьи — \<статья>** укажите одно из следующих значений для параметра **Репликация**.  
  
    -   **Выполнение хранимой процедуры**  
  
    -   **Выполнение в сериализованной транзакции хранимой процедуры**  
  
         Это рекомендуемый параметр, поскольку он реплицирует выполнение процедуры только в случае ее выполнения в контексте сериализуемой транзакции. При выполнении хранимой процедуры вне сериализуемой транзакции изменения, вносимые в данные опубликованных таблиц, реплицируются как ряды инструкций языка обработки данных.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
## <a name="see-also"></a>См. также:  
 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
