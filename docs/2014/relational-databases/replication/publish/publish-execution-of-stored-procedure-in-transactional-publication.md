---
title: Публикация выполнения хранимой процедуры в публикации транзакций (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a226d7c58b3b72caf415d8e873b58ca38d3c749f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060426"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>опубликовать выполнение хранимой процедуры в публикации транзакций (среда SQL Server Management Studio)
  Укажите, что выполнение хранимой процедуры (а не только ее определение) должно быть опубликовано в диалоговом окне **Свойства статьи \<Article> —** . Это диалоговое окно доступно в мастере создания публикаций и в диалоговом окне **Свойства публикации — \<Publication> ** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](create-a-publication.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
 Определение процедуры (инструкция CREATE PROCEDURE) реплицируется на подписчик при инициализации подписки. Когда процедура выполняется на издателе, репликация выполняет соответствующую процедуру на подписчике.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Публикация выполнения хранимой процедуры  
  
1.  На странице **статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Publication> ** выберите хранимую процедуру.  
  
2.  Щелкните **Свойства статьи**, а затем щелкните **Задать свойства выделенной хранимой процедуры**.  
  
3.  В диалоговом окне **свойства \<Article> статьи —** укажите одно из следующих значений параметра **реплицировать** .  
  
    -   **Выполнение хранимой процедуры**  
  
    -   **Выполнение в сериализованной транзакции хранимой процедуры.**  
  
         Это рекомендуемый параметр, поскольку он реплицирует выполнение процедуры только в случае ее выполнения в контексте сериализуемой транзакции. При выполнении хранимой процедуры вне сериализуемой транзакции изменения, вносимые в данные опубликованных таблиц, реплицируются как ряды инструкций языка обработки данных.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  В диалоговом окне **Свойства публикации — \<Publication> ** нажмите кнопку **ОК** , чтобы сохранить и закрыть диалоговое окно.  
  
## <a name="see-also"></a>См. также:  
 [Публикация выполнения хранимых процедур в репликации транзакций](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
