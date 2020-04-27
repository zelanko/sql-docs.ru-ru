---
title: Подписка базы данных на категорию политики или отмена подписки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d0139376adc28b07877389a023b19310b06417ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68212131"
---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a>Подписка базы данных на категорию политики или отмена подписки
  В этом разделе описывается подписка и отмена подписки базы данных на категорию политики в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для подписки базы данных на категорию политики или отмены подписки используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a>Подписка базы данных на категорию политики или отмена подписки  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть базу данных, в которой нужно изменить подписки на категории.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Базы данных** .  
  
3.  Щелкните правой кнопкой мыши базу данных, в которой нужно изменить подписки на категории, укажите пункт **Политики**и выберите пункт **Категории**.  
  
     В диалоговом окне **Категории** доступны следующие параметры.  
  
     Развернуть столбец  
     Щелкните, чтобы развернуть категорию политики. Перечисляет все политики, включенные в категорию.  
  
     **Имя**  
     Имя категории политики.  
  
     **Подписаны**  
     Указывает, имеет ли цель подписку на категорию политики. Если этот флажок не установлен, то категория политики задается для варианта **Обязательные подписки базы данных**. Это означает, что категория политики может применяться ко всем базам данных на сервере.  
  
     **Политика**  
     Если группы политик развернуты, отображаются политики в категории политики.  
  
     **Включен**  
     Указывает, включены или выключены политики.  
  
     **Режим выполнения**  
     Отображает режим выполнения политики.  
  
     **Журнал**  
     Перейдите по гиперссылке «Просмотр журнала», чтобы открыть средство просмотра файлов журнала и просмотреть журнал политики.  
  
4.  Чтобы подписаться на категорию управления на основе политик, установите флажок категории в столбце **Подписка** . Чтобы отменить подписку на категорию, снимите флажок.  
  
5.  По окончании нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
  
 Дополнительные сведения см. в статье [sp_syspolicy_subscribe_to_policy_category (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql).  
  
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
  
 Дополнительные сведения см. в статье [sp_syspolicy_unsubscribe_from_policy_category (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql).  
  
  
