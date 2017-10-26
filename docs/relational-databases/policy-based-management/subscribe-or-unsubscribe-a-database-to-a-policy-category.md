---
title: "Подписка базы данных на категорию политики или отмена подписки | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 56ad4058339f59a69409ef1c0319f9b41354823c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a>Подписка базы данных на категорию политики или отмена подписки
  В этом разделе описывается подписка и отмена подписки базы данных на категорию политики в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Для подписки базы данных на категорию политики или отмены подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a>Подписка базы данных на категорию политики или отмена подписки  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть базу данных, в которой нужно изменить подписки на категории.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Базы данных** .  
  
3.  Щелкните правой кнопкой мыши базу данных, в которой нужно изменить подписки на категории, укажите пункт **Политики**и выберите пункт **Категории**.  
  
     В диалоговом окне **Категории** доступны следующие параметры.  
  
     Развернуть столбец  
     Щелкните, чтобы развернуть категорию политики. Перечисляет все политики, включенные в категорию.  
  
     **Название**  
     Имя категории политики.  
  
     **Есть подписка**  
     Указывает, имеет ли цель подписку на категорию политики. Если этот флажок не установлен, то категория политики задается для варианта **Обязательные подписки базы данных**. Это означает, что категория политики может применяться ко всем базам данных на сервере.  
  
     **политика**  
     Если группы политик развернуты, отображаются политики в категории политики.  
  
     **Включено**  
     Указывает, включены или выключены политики.  
  
     **Режим выполнения**  
     Отображает режим выполнения политики.  
  
     **Журнал**  
     Перейдите по гиперссылке «Просмотр журнала», чтобы открыть средство просмотра файлов журнала и просмотреть журнал политики.  
  
4.  Чтобы подписаться на категорию управления на основе политик, установите флажок категории в столбце **Подписка** . Чтобы отменить подписку на категорию, снимите флажок.  
  
5.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-subscribe-a-database-to-a-policy-category"></a>Подписка базы данных на категорию политики  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 Дополнительные сведения см. в статье [sp_syspolicy_subscribe_to_policy_category (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql.md).  
  
#### <a name="to-unsubscribe-a-database-to-a-policy-category"></a>Отмена подписки базы данных на категорию политики  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 Дополнительные сведения см. в статье [sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md).  
  
  

