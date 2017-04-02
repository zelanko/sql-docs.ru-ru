---
title: "Установка срока действия подписок | Microsoft Docs"
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
  - "подписки [репликация SQL Server], истечение срока действия"
  - "срок действия [репликация SQL Server]"
  - "срок хранения [репликация SQL Server]"
  - "отключение подписок"
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Установка срока действия подписок
  В этом разделе описывается установка срока действия подписок в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Срок действия подписок определяет период времени до истечения и удаления подписки. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для установки срока действия подписок используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Срок действия подписки также может называться *сроком хранения публикации*. Очистка метаданных репликации слиянием зависит от этой настройки:  
  
    -   Репликации не удастся очистить метаданные в базах данных публикации и подписки, пока не закончится срок хранения. Будьте осмотрительны при указании больших значений срока хранения, так как они могут негативно сказываться на производительности репликации. Рекомендуется использовать небольшие значения, если можно надежно предсказать, что все подписчики будут синхронизироваться регулярно в течение указанного периода времени.  
  
         Срок хранения для публикаций слиянием содержит 24-часовой льготный период для размещения подписчиков в разных часовых поясах. Например, если установить срок хранения продолжительностью в один день, то действительный срок хранения будет равен 48 часам.  
  
    -   Можно задать неограниченный срок действия подписок, но настоятельно рекомендуется не использовать такое значение, так как нельзя будет очистить метаданные.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Установка срока действия для подписок на **Общие** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Установка срока действия подписок  
  
1.  В **истечения срока действия подписки** статьи на **Общие** страницы **Свойства публикации — \< публикация>** диалогового окна укажите, следует ли срок действия подписки.  
  
2.  Если срок действия подписок должен быть ограничен, задайте время, по истечении которого подписки перестают действовать.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно использовать хранимые процедуры репликации, чтобы задать это значение при создании публикации, либо изменить это значение позднее.  
  
#### Настройка срока действия подписки на моментальный снимок или публикацию транзакций  
  
1.  На издателе, хранимую [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Укажите нужный срок действия подписки в часах в параметре **@retention**. По умолчанию срок хранения равен 336 часам. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Настройка срока действия подписки на публикацию слиянием  
  
1.  На издателе, хранимую [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите нужный срок действия подписки в параметре **@retention**. Укажите единицы измерения, в которых выражается срока действия для **@retention_period_unit**, который может принимать одно из следующих:  
  
    -   **1** = неделя  
  
    -   **2** = месяц  
  
    -   **3** = год  
  
     По умолчанию срок хранения равен 14 дням. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Изменение срока действия подписки на моментальный снимок или публикацию транзакций  
  
1.  На издателе, хранимую [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Укажите значение **retention** в параметре **@property** и новый срок действия подписки в часах в параметре **@value**.  
  
#### Изменение срока действия подписки на публикацию слиянием  
  
1.  На издателе, хранимую [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав **@publication** и **@publisher**. Обратите внимание на значение **retention_period_unit** в результирующем наборе, который может быть одним из следующих:  
  
    -   **0** = день  
  
    -   **1** = неделя  
  
    -   **2** = месяц  
  
    -   **3** = год  
  
2.  На издателе, хранимую [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Укажите значение **retention** в параметре **@property** и новый срок действия подписки в виде текста на основе единицы измерения срока хранения из шага 1 в параметре **@value**.  
  
3.  (Необязательно) На издателе, хранимую [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Укажите **retention_period_unit** для **@property** и новую единицу измерения для срока действия подписки **@value**.  
  
## См. также:  
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Окончание срока действия и отключение подписки](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  