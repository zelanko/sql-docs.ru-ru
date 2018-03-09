---
title: "Повторное создание пользовательских процедур транзакций с учетом изменений в схеме | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
caps.latest.revision: "29"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d1b90d1717e68e9e140b52d401f8e02ba2eccc0
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="transactional-articles---regenerate-to-reflect-schema-changes"></a>Повторное создание транзакционных статей с учетом изменений в схеме
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] По умолчанию репликация транзакций осуществляет изменение всех данных подписчика через хранимые процедуры, формируемые внутренними процедурами для каждой статьи таблицы в публикации. Эти три процедуры (по одной для вставок, обновлений и удалений) копируются на подписчик и выполняются при репликации вставки, обновления или удаления на подписчик. Если изменение схемы вносится в таблицу на издателе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , репликация автоматически заново формирует эти процедуры, вызывая тот же набор внутренних процедур сценария, чтобы новые процедуры соответствовали новой схеме (репликация изменений схемы не поддерживается для издателей Oracle).  
  
 Также можно задать пользовательские процедуры для замены одной или нескольких процедур по умолчанию. Пользовательские процедуры должны изменяться, если на них влияет изменение схемы. Например если процедура ссылается на столбец, удаленный при изменении схемы, то ссылки на этот столбец должны быть удалены из пользовательской процедуры. Имеется два способа, которыми репликация может передавать новую пользовательскую процедуру подписчикам:  
  
-   Первый — это использовать пользовательскую процедуру сценария для замены процедур репликации.  
  
    1.  При выполнении процедуры [sp_addarticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) бит **@schema_option** 0x02 должен иметь значение **true**.  
  
    2.  Выполните процедуру [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md), указав значение 'insert', 'update' или 'delete' для параметра **@type**, а также имя пользовательской процедуры скрипта в качестве значения для параметра **@value**.  
  
     При следующем изменении схемы репликация вызывает эту хранимую процедуру, чтобы создать скрипт определения для новой пользовательской хранимой процедуры, а затем передает ее всем подписчикам.  
  
-   Второй способ состоит в использовании скрипта, содержащего определение новой пользовательской процедуры:  
  
    1.  При выполнении процедуры [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) установите бит **@schema_option** в значение **false**, чтобы репликация не формировала пользовательские процедуры на стороне подписчика автоматически.  
  
    2.  Перед каждым изменением схемы создавайте новый файл скрипта и регистрируйте скрипт в репликации, выполняя процедуру [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Укажите значение custom_script для параметра **@type** и путь к этому скрипту у издателя для параметра **@value**.  
  
     При следующем изменении соответствующей схемы этот скрипт выполняется у каждого подписчика в той же транзакции, что и команда DDL. После завершения изменений схемы регистрация скрипта отменяется. Чтобы этот скрипт выполнялся при последующем изменении схемы, его необходимо повторно зарегистрировать.  
  
## <a name="see-also"></a>См. также:  
 [Указание способа распространения изменений для статей транзакций](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Внесение изменений в схемы баз данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
