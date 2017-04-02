---
title: "Репликация изменений схемы | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "репликация [SQL Server], изменения схемы"
  - "схемы [репликация SQL Server], репликация изменений"
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Репликация изменений схемы
  В этом разделе описывается процесс репликации изменений схемы в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Если в опубликованную статью внести следующие изменения схемы, они по умолчанию распространяются на подписчики [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
-   **Для репликации изменений схемы используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Инструкция ALTER TABLE … DROP COLUMN всегда реплицируется для всех подписчиков, чьи подписки содержат удаляемые столбцы, даже при отключенной репликации изменений схемы.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Если вы не хотите реплицировать изменения схемы для публикации, отключите репликацию изменений схемы в **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Отключение репликации изменений схемы  
  
1.  На **Параметры подписки** Страница **Свойства публикации — \< публикация>** диалоговое окно установите значение **реплицировать изменения схемы** Свойства **False**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Для распространения только определенных изменений схемы перед изменением схемы установите свойство в **True** , а после выполнения изменений установите его в **False** . И наоборот, для распространения всех изменений схемы, за исключением данного изменения, перед изменением схемы установите свойство в **False** , а после выполнения изменений установите его в **True** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно использовать хранимые процедуры репликации для указания, следует ли реплицировать эти изменения схемы. Используемая хранимая процедура зависит от типа публикации.  
  
#### Создание публикации моментальных снимков или публикации транзакций без репликации изменений схемы  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), указав значение **0** для **@replicate_ddl**. Дополнительные сведения см. в статье [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Создание публикации слиянием без репликации изменений схемы  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), указав значение **0** для **@replicate_ddl**. Дополнительные сведения см. в статье [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Временное отключение репликации изменений схемы для публикации моментальных снимков или публикации транзакций  
  
1.  Для публикации с помощью репликации изменений схемы, выполнение [sp_changepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав значение **replicate_ddl** для **@property** и значение **0** для **@value**.  
  
2.  Выполните команду DDL на опубликованном объекте.  
  
3.  (Необязательно) Включить репликацию изменений схемы, выполнив [sp_changepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав значение **replicate_ddl** для **@property** и значение **1** для **@value**.  
  
#### Временное отключение репликации изменений схемы для публикации слиянием  
  
1.  Для публикации с помощью репликации изменений схемы, выполнение [sp_changemergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав значение **replicate_ddl** для **@property** и значение **0** для **@value**.  
  
2.  Выполните команду DDL на опубликованном объекте.  
  
3.  (Необязательно) Включить репликацию изменений схемы, выполнив [sp_changemergepublication & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав значение **replicate_ddl** для **@property** и значение **1** для **@value**.  
  
## См. также:  
 [Внесение изменений схем в базы данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Внесение изменений схем в базы данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  