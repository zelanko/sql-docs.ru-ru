---
title: "База данных публикации | Документация Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3f29e1319d78cb2fadca134b78abdfc748e11c67
ms.lasthandoff: 04/11/2017

---
# <a name="publication-database"></a>База данных публикации
  База данных публикации — это база данных на издателе, которая является источником данных и объектов базы данных, предназначенных для репликации. Необходимо задействовать все базы данных публикации, которые будут использоваться в репликации. База данных задействуется, если элемент предопределенной роли сервера **sysadmin** выполняет следующие действия:  
  
-   создает публикацию в этой базе данных с помощью мастера создания публикаций;  
  
-   выбирает базу данных в диалоговом окне **Свойства издателя** ;  
  
-   выполняет процедуру **sp_replicationdboption** и присваивает параметрам **publish** (для моментальных снимков или публикаций транзакций) или **merge publish** (для публикаций слиянием) значение **True**.  
  
## <a name="options"></a>Параметры  
 **Базы данных**  
 Выберите имя базы данных, содержащее данные и объекты базы данных, которое нужно опубликовать.  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
