---
title: Предоставление пользователям без прав администратора разрешений на использование монитора репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068646"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>Предоставление пользователям без прав администратора разрешения на использование монитора репликации
  В этом разделе показано, как разрешить пользователям без прав администратора использовать монитор репликации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Монитор репликации может использоваться пользователями, которые являются членами следующих ролей:  
  
-   Предопределенная роль сервера **sysadmin** .  
  
     Такие пользователи могут выполнять наблюдение за репликацией и полностью контролировать процессы внесения изменений в свойства репликации, а именно: расписания работы агентов, профили агентов и т. д.  
  
-   `replmonitor`Роль базы данных в базе данных распространителя.  
  
     Такие пользователи могут выполнять наблюдение за репликацией, но не могут вносить изменения ни в какие свойства репликации.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для предоставления пользователям без прав администратора разрешения на использование монитора репликации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Чтобы разрешить пользователям без прав администратора использовать монитор репликации, член предопределенной роли сервера **sysadmin** должен добавить пользователя в базу данных распространителя и назначить его `replmonitor` роли.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>Предоставление пользователям без прав администратора разрешения на использование монитора репликации  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]подключитесь к распространителю, а затем разверните узел сервера.  
  
2.  Последовательно раскройте **Базы данных**, **Системные базы данных**и раскройте базу данных распространителя (по умолчанию называемую **distribution** ).  
  
3.  Раскройте **Безопасность**, щелкните правой кнопкой **Пользователь**, а затем выберите **Создать пользователя...**.  
  
4.  Введите имя пользователя и имя входа.  
  
5.  Выберите схему по умолчанию `replmonitor` .  
  
6.  Установите `replmonitor` флажок в сетке **членство в роли базы данных** .  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>Добавление пользователя к предопределенной роли «replmonitor» базы данных  
  
1.  В базе данных на распространителе выполните процедуру [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql). Если пользователь не перечислен в `UserName` результирующем наборе, ему должен быть предоставлен доступ к базе данных распространителя с помощью инструкции [CREATE USER &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) .  
  
2.  На распространителе в базе данных распространителя выполните [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), указав значение `replmonitor` для **@rolename** параметра. Если пользователь перечислен в `MemberName` результирующем наборе, он уже принадлежит этой роли.  
  
3.  Если пользователь не принадлежит `replmonitor` роли, выполните [Sp_addrolemember &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) на распространителе в базе данных распространителя. Укажите значение `replmonitor` для **@rolename** , а также имя пользователя базы данных или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] логин Windows, добавляемый для **@membername** .  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>Удаление пользователя из предопределенной роли «replmonitor» базы данных  
  
1.  Чтобы убедиться, что пользователь принадлежит к `replmonitor` роли, выполните [Sp_helprolemember &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) на распространителе в базе данных распространителя и укажите значение `replmonitor` для параметра **@rolename** . Если пользователь не указан в поле `MemberName` результирующего набора, в данный момент он не принадлежит этой роли.  
  
2.  Если пользователь принадлежит к `replmonitor` роли, выполните [Sp_droprolemember &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) на распространителе в базе данных распространителя. Укажите значение `replmonitor` для **@rolename** , а также имя пользователя базы данных или имени входа Windows, которое удаляется для **@membername** .  
  
  
