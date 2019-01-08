---
title: База данных публикации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb31bae59d95b01279a9fa84e02cd22c8017ca14
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52789386"
---
# <a name="publication-database"></a>База данных публикации
  База данных публикации — это база данных на издателе, которая является источником данных и объектов базы данных, предназначенных для репликации. Необходимо задействовать все базы данных публикации, которые будут использоваться в репликации. База данных задействуется, если элемент предопределенной роли сервера **sysadmin** выполняет следующие действия:  
  
-   создает публикацию в этой базе данных с помощью мастера создания публикаций;  
  
-   выбирает базу данных в диалоговом окне **Свойства издателя** ;  
  
-   выполняет процедуру **sp_replicationdboption** и присваивает параметрам **publish** (для моментальных снимков или публикаций транзакций) или **merge publish** (для публикаций слиянием) значение **True**.  
  
## <a name="options"></a>Параметры  
 **Базы данных**  
 Выберите имя базы данных, содержащее данные и объекты базы данных, которое нужно опубликовать.  
  
## <a name="see-also"></a>См. также  
 [Публикация данных и объектов базы данных](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
