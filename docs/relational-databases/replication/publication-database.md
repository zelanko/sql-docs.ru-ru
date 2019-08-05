---
title: База данных публикации | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 38694dfd2eadb4b25c2606bc825f5388e48daf29
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770063"
---
# <a name="publication-database"></a>База данных публикации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  База данных публикации — это база данных на издателе, которая является источником данных и объектов базы данных, предназначенных для репликации. Необходимо задействовать все базы данных публикации, которые будут использоваться в репликации. База данных задействуется, если элемент предопределенной роли сервера **sysadmin** выполняет следующие действия:  
  
-   создает публикацию в этой базе данных с помощью мастера создания публикаций;  
  
-   выбирает базу данных в диалоговом окне **Свойства издателя** ;  
  
-   выполняет процедуру **sp_replicationdboption** и присваивает параметрам **publish** (для моментальных снимков или публикаций транзакций) или **merge publish** (для публикаций слиянием) значение **True**.  
  
## <a name="options"></a>Параметры  
 **Базы данных**  
 Выберите имя базы данных, содержащее данные и объекты базы данных, которое нужно опубликовать.  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
