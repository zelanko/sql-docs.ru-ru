---
title: "Предоставление пользователям без прав администратора разрешений на использование монитора репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 95a0b865d33d96b740a48971bfccbc1334b37807
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>Предоставление пользователям без прав администратора разрешения на использование монитора репликации
  В этом разделе показано, как разрешить пользователям без прав администратора использовать монитор репликации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Монитор репликации может использоваться пользователями, которые являются членами следующих ролей:  
  
-   Предопределенная роль сервера **sysadmin** .  
  
     Такие пользователи могут выполнять наблюдение за репликацией и полностью контролировать процессы внесения изменений в свойства репликации, а именно: расписания работы агентов, профили агентов и т. д.  
  
-   Роль базы данных **replmonitor** в базе данных распространителя.  
  
     Такие пользователи могут выполнять наблюдение за репликацией, но не могут вносить изменения ни в какие свойства репликации.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Для предоставления пользователям без прав администратора разрешения на использование монитора репликации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Чтобы разрешить пользователям без прав администратора использовать монитор репликации, член предопределенной роли сервера **sysadmin** должен добавить пользователя в базу данных распространителя и присвоить такому пользователю роль **replmonitor** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>Предоставление пользователям без прав администратора разрешения на использование монитора репликации  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]подключитесь к распространителю, а затем разверните узел сервера.  
  
2.  Последовательно раскройте **Базы данных**, **Системные базы данных**и раскройте базу данных распространителя (по умолчанию называемую **distribution** ).  
  
3.  Раскройте **Безопасность**, щелкните правой кнопкой **Пользователь**, а затем выберите **Создать пользователя...**.  
  
4.  Введите имя пользователя и имя входа.  
  
5.  Выберите схему **replmonitor**, заданную по умолчанию.  
  
6.  Установите флажок **replmonitor** в сетке **Членство в роли базы данных** .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>Добавление пользователя к предопределенной роли «replmonitor» базы данных  
  
1.  В базе данных на распространителе выполните процедуру [sp_helpuser &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md). Если пользователь не указан в поле **UserName** итогового набора, ему следует предоставить доступ к базе данных распространителя с помощью инструкции [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md).  
  
2.  В базе данных распространителя на распространителе выполните процедуру [sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md), указав значение **replmonitor** в параметре **@rolename**. Если пользователь указан в поле **MemberName** результирующего набора, он уже принадлежит этой роли.  
  
3.  Если пользователь не принадлежит роли **replmonitor**, выполните процедуру [sp_addrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) в базе данных распространителя на распространителе. Укажите значение **replmonitor** для **@rolename** , а также добавляемое имя пользователя базы данных или имя входа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows для **@membername**.  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>Удаление пользователя из предопределенной роли «replmonitor» базы данных  
  
1.  Чтобы убедиться, что пользователь принадлежит роли **replmonitor**, выполните в базе данных распространителя на распространителе процедуру [sp_helprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) и задайте значение **replmonitor** для параметра **@rolename**. Если пользователь не указан в поле **MemberName** результирующего набора, в данный момент он не принадлежит этой роли.  
  
2.  Если пользователь принадлежит роли **replmonitor**, выполните процедуру [sp_droprolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) в базе данных распространителя на распространителе. Укажите значение **replmonitor** для **@rolename** , а также имя пользователя базы данных или имя входа Windows, подлежащее удалению, для **@membername**.  
  
  
