---
title: Публикация выполнения хранимой процедуры (транзакции)
description: Узнайте, как опубликовать выполнение хранимых процедур с помощью SQL Server Management Studio.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 58d5393e95c1ab12d2815799a25267ea4c84958c
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914610"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>Публикация выполнения хранимой процедуры в публикации транзакций
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Укажите, что выполнение хранимой процедуры (а не просто ее определение) следует опубликовывать в диалоговом окне **Свойства статьи — \<Article>** . Это диалоговое окно доступно в мастере создания публикаций и в диалоговом окне **Свойства публикации — \<Publication>** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Определение процедуры (инструкция CREATE PROCEDURE) реплицируется на подписчик при инициализации подписки. Когда процедура выполняется на издателе, репликация выполняет соответствующую процедуру на подписчике.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Публикация выполнения хранимой процедуры  
  
1.  Выберите хранимую процедуру на странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Publication>** .  
  
2.  Щелкните **Свойства статьи**, а затем щелкните **Задать свойства выделенной хранимой процедуры**.  
  
3.  В диалоговом окне **Свойства статьи —\<Article>** укажите одно из следующих значений для параметра **Репликация**.  
  
    -   **Выполнение хранимой процедуры**  
  
    -   **Выполнение в сериализованной транзакции хранимой процедуры**  
  
         Это рекомендуемый параметр, поскольку он реплицирует выполнение процедуры только в случае ее выполнения в контексте сериализуемой транзакции. При выполнении хранимой процедуры вне сериализуемой транзакции изменения, вносимые в данные опубликованных таблиц, реплицируются как ряды инструкций языка обработки данных.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Publication>** , нажмите кнопку **OK**, чтобы сохранить результаты и закрыть диалоговое окно.  
  
## <a name="see-also"></a>См. также:  
 [Публикация выполнения хранимых процедур в репликации транзакций](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
