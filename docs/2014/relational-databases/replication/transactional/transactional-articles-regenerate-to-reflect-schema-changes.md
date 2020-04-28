---
title: Повторное создание пользовательских процедур транзакций с учетом изменений в схеме | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 8a99a98fd0d471e8cb0f8ab880ae1a6c55e1b121
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62655509"
---
# <a name="regenerate-custom-transactional-procedures-to-reflect-schema-changes"></a>Повторное создание пользовательских процедур транзакций для отражения изменений схем
  По умолчанию репликация транзакций выполняет изменение всех данных подписчика через хранимые процедуры, сформированные внутренними процедурами для каждой статьи таблицы в публикации. Эти три процедуры (по одной для вставок, обновлений и удалений) копируются на подписчик и выполняются при репликации вставки, обновления или удаления на подписчик. Если изменение схемы вносится в таблицу на издателе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , репликация автоматически заново формирует эти процедуры, вызывая тот же набор внутренних процедур сценария, чтобы новые процедуры соответствовали новой схеме (репликация изменений схемы не поддерживается для издателей Oracle).  
  
 Также можно задать пользовательские процедуры для замены одной или нескольких процедур по умолчанию. Пользовательские процедуры должны изменяться, если на них влияет изменение схемы. Например если процедура ссылается на столбец, удаленный при изменении схемы, то ссылки на этот столбец должны быть удалены из пользовательской процедуры. Имеется два способа, которыми репликация может передавать новую пользовательскую процедуру подписчикам:  
  
-   Первый — это использовать пользовательскую процедуру сценария для замены процедур репликации.  
  
    1.  При выполнении [sp_addarticle &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)убедитесь, что **@schema_option** бит 0x02 имеет **значение true**.  
  
    2.  Выполните [sp_register_custom_scripting &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql) и укажите значение "Insert", "Update" или "Delete" для параметра **@type** и имя пользовательской процедуры создания скрипта для параметра. **@value**  
  
     При следующем изменении схемы репликация вызывает эту хранимую процедуру, чтобы создать скрипт определения для новой пользовательской хранимой процедуры, а затем передает ее всем подписчикам.  
  
-   Второй способ состоит в использовании скрипта, содержащего определение новой пользовательской процедуры:  
  
    1.  При выполнении [sp_addarticle &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)установите бит **@schema_option** 0x02 в **значение false** , чтобы репликация не создавала автоматически пользовательские процедуры на подписчике.  
  
    2.  Перед каждым изменением схемы создавайте новый файл скрипта и регистрируйте скрипт в репликации, выполняя процедуру [sp_register_custom_scripting &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql). Укажите значение "custom_script" для параметра **@type** и путь к скрипту на издателе для параметра. **@value**  
  
     При следующем изменении соответствующей схемы этот скрипт выполняется у каждого подписчика в той же транзакции, что и команда DDL. После завершения изменений схемы регистрация скрипта отменяется. Чтобы этот скрипт выполнялся при последующем изменении схемы, его необходимо повторно зарегистрировать.  
  
## <a name="see-also"></a>См. также  
 [Укажите, как изменения распространяются для транзакционных статей](transactional-articles-specify-how-changes-are-propagated.md)   
 [Внесение изменений схем в базы данных публикации](../publish/make-schema-changes-on-publication-databases.md)  
  
  
