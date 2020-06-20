---
title: Установка срока действия подписок | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc0ecb449af64b88cf3ded032c78c2e399dd4234
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060365"
---
# <a name="set-the-expiration-period-for-subscriptions"></a>Установка срока действия подписок
  В этом разделе описывается установка срока действия подписок в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Срок действия подписок определяет период времени до истечения и удаления подписки. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для установки срока действия подписок используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Срок действия подписки также может называться *сроком хранения публикации*. Очистка метаданных репликации слиянием зависит от этой настройки:  
  
    -   Репликации не удастся очистить метаданные в базах данных публикации и подписки, пока не закончится срок хранения. Будьте осмотрительны при указании больших значений срока хранения, так как они могут негативно сказываться на производительности репликации. Рекомендуется использовать небольшие значения, если можно надежно предсказать, что все подписчики будут синхронизироваться регулярно в течение указанного периода времени.  
  
         Срок хранения для публикаций слиянием содержит 24-часовой льготный период для размещения подписчиков в разных часовых поясах. Например, если установить срок хранения продолжительностью в один день, то действительный срок хранения будет равен 48 часам.  
  
    -   Можно задать неограниченный срок действия подписок, но настоятельно рекомендуется не использовать такое значение, так как нельзя будет очистить метаданные.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Задайте срок действия подписок на странице **Общие** диалогового окна **Свойства публикации — \<Publication> ** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a>Установка срока действия подписок  
  
1.  В разделе **срок действия подписки** на странице **Общие** диалогового окна **Свойства публикации — \<Publication> ** укажите, истечет ли срок действия подписок.  
  
2.  Если срок действия подписок должен быть ограничен, задайте время, по истечении которого подписки перестают действовать.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно использовать хранимые процедуры репликации, чтобы задать это значение при создании публикации, либо изменить это значение позднее.  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a>Настройка срока действия подписки на моментальный снимок или публикацию транзакций  
  
1.  Выполните процедуру [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)на издателе. Укажите нужный срок действия подписки в часах в параметре **\@retention**. По умолчанию срок хранения равен 336 часам. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a>Настройка срока действия подписки на публикацию слиянием  
  
1.  Выполните процедуру [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)на издателе. Укажите нужный срок действия подписки в параметре **\@retention**. Укажите единицы измерения, в которых выражается период хранения, в параметре **\@retention_period_unit**. Возможны следующие варианты:  
  
    -   **1** = Неделя  
  
    -   **2** = Месяц  
  
    -   **3** = Год  
  
     По умолчанию срок хранения равен 14 дням. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a>Изменение срока действия подписки на моментальный снимок или публикацию транзакций  
  
1.  На издателе выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Укажите значение **retention** в параметре **\@property** и новый срок действия подписки в часах в параметре **\@value**.  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a>Изменение срока действия подписки на публикацию слиянием  
  
1.  В издателе выполните хранимую процедуру [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), указав параметры **\@publication** и **\@publisher**. Запомните значение **retention_period_unit** в результирующем наборе, которое может быть одним из следующих:  
  
    -   **0** = сутки;  
  
    -   **1** = Неделя  
  
    -   **2** = Месяц  
  
    -   **3** = Год  
  
2.  На издателе выполните хранимую процедуру [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Укажите значение **retention** в параметре **\@property** и новый срок действия подписки в виде текста на основе единицы измерения срока хранения из шага 1 в параметре **\@value**.  
  
3.  (Необязательно) На издателе выполните хранимую процедуру [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Укажите значение **retention_period_unit** в параметре **\@property** и новую единицу измерения для срока действия подписки в параметре **\@value**.  
  
## <a name="see-also"></a>См. также:  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Окончание срока действия и отключение подписки](../subscription-expiration-and-deactivation.md)  
  
  
