---
title: "Управление табличными пространствами Oracle | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6a685337d7aeb6dbf388faec93051ce29cc5759
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="manage-oracle-tablespaces"></a>Управление табличными пространствами Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Табличное пространство — это единица хранилища базы данных, приблизительно эквивалентная группе файлов в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Табличные пространства предоставляют возможности хранения и управления объектами баз данных в рамках индивидуальных групп. Дополнительные сведения см. в документации Oracle.  
  
 При настройке таблицы как части публикации Oracle можно при желании указать, что существующее табличное пространство Oracle будет использоваться для хранения информации о ходе репликации. В противном случае табличным пространством для объектов репликации будет табличное пространство по умолчанию, связанное с административной пользовательской схемой репликации, которая была настроена при настройке издателя.  
  
 **Указание табличного пространства для таблицы регистрации статей**:  
  
-   Задайте табличное пространство в диалоговом окне **Свойства статьи** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Используйте [sp_changearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Чтобы использовать **sp_changearticle**, укажите следующее:  
  
    -   имя издателя Oracle в качестве параметра **@publisher**.  
  
    -   имя публикации Oracle в качестве параметра **@publication**.  
  
    -   имя статьи в качестве параметра **@article**.  
  
    -   значение tablespace для параметра **@property**.  
  
    -   имя табличного пространства для параметра **@value**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Objects Created on the Oracle Publisher](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)  
  
  
