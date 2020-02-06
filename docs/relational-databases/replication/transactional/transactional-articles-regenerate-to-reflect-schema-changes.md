---
title: Повторное создание пользовательских процедур для отражения изменений схем (транзакции)
description: Повторное создание пользовательских хранимых процедур транзакций с учетом изменений в схеме для транзакционной репликации.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: e20f38a055fba642795ed0c0d40d07cbff442a9b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287005"
---
# <a name="transactional-articles---regenerate-to-reflect-schema-changes"></a>Повторное создание транзакционных статей с учетом изменений в схеме
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  По умолчанию репликация транзакций выполняет изменение всех данных подписчика через хранимые процедуры, сформированные внутренними процедурами для каждой статьи таблицы в публикации. Эти три процедуры (по одной для вставок, обновлений и удалений) копируются на подписчик и выполняются при репликации вставки, обновления или удаления на подписчик. Если изменение схемы вносится в таблицу на издателе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , репликация автоматически заново формирует эти процедуры, вызывая тот же набор внутренних процедур сценария, чтобы новые процедуры соответствовали новой схеме (репликация изменений схемы не поддерживается для издателей Oracle).  
  
 Также можно задать пользовательские процедуры для замены одной или нескольких процедур по умолчанию. Пользовательские процедуры должны изменяться, если на них влияет изменение схемы. Например если процедура ссылается на столбец, удаленный при изменении схемы, то ссылки на этот столбец должны быть удалены из пользовательской процедуры. Имеется два способа, которыми репликация может передавать новую пользовательскую процедуру подписчикам:  
  
-   Первый — это использовать пользовательскую процедуру сценария для замены процедур репликации.  
  
    1.  При выполнении процедуры [sp_addarticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) бит `@schema_option` 0x02 должен иметь значение **true**.  
  
    2.  Выполните процедуру [sp_register_custom_scripting (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md), указав значение insert, update или delete для параметра `@type`, а также имя пользовательской процедуры скрипта в качестве значения для параметра `@value`.  
  
     При следующем изменении схемы репликация вызывает эту хранимую процедуру, чтобы создать скрипт определения для новой пользовательской хранимой процедуры, а затем передает ее всем подписчикам.  
  
-   Второй способ состоит в использовании скрипта, содержащего определение новой пользовательской процедуры:  
  
    1.  При выполнении процедуры [sp_addarticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) установите бит `@schema_option` равным **false**, чтобы репликация не формировала пользовательские процедуры на стороне подписчика автоматически.  
  
    2.  Перед каждым изменением схемы создавайте новый файл скрипта и регистрируйте скрипт в репликации, выполняя процедуру [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Укажите значение custom_script для параметра `@type` и путь к этому скрипту у издателя для параметра `@value`.  
  
     При следующем изменении соответствующей схемы этот скрипт выполняется у каждого подписчика в той же транзакции, что и команда DDL. После завершения изменений схемы регистрация скрипта отменяется. Чтобы этот скрипт выполнялся при последующем изменении схемы, его необходимо повторно зарегистрировать.  
  
## <a name="see-also"></a>См. также:  
 [Указание способа распространения изменений для статей транзакций](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Внесение изменений в схемы баз данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
