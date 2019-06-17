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
manager: craigg
ms.openlocfilehash: 9e8f03d12d3ac1695d4f6d000c8eab89a42004fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62667392"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a>Предоставление пользователям без прав администратора разрешения на использование монитора репликации
  В этом разделе показано, как разрешить пользователям без прав администратора использовать монитор репликации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Монитор репликации может использоваться пользователями, которые являются членами следующих ролей:  
  
-   Предопределенная роль сервера **sysadmin** .  
  
     Такие пользователи могут выполнять наблюдение за репликацией и полностью контролировать процессы внесения изменений в свойства репликации, а именно: расписания работы агентов, профили агентов и т. д.  
  
-   `replmonitor` Роли базы данных в базе данных распространителя.  
  
     Такие пользователи могут выполнять наблюдение за репликацией, но не могут вносить изменения ни в какие свойства репликации.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для предоставления пользователям без прав администратора разрешения на использование монитора репликации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Чтобы разрешить пользователям без прав администратора использовать монитор репликации, член **sysadmin** предопределенной роли сервера необходимо добавить пользователя в базу данных распространителя и присвоить такому пользователю `replmonitor` роли.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a>Предоставление пользователям без прав администратора разрешения на использование монитора репликации  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]подключитесь к распространителю, а затем разверните узел сервера.  
  
2.  Последовательно раскройте **Базы данных**, **Системные базы данных**и раскройте базу данных распространителя (по умолчанию называемую **distribution** ).  
  
3.  Раскройте **Безопасность**, щелкните правой кнопкой **Пользователь**, а затем выберите **Создать пользователя...** .  
  
4.  Введите имя пользователя и имя входа.  
  
5.  Выберите схему по умолчанию `replmonitor`.  
  
6.  Выберите `replmonitor` флажок в **членство в роли базы данных** сетки.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a>Добавление пользователя к предопределенной роли «replmonitor» базы данных  
  
1.  В базе данных на распространителе выполните процедуру [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql). Если пользователь не указан в `UserName` в результирующем наборе, пользователь должен быть предоставлен доступ к базе данных распространителя с помощью [CREATE USER &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-user-transact-sql) инструкции.  
  
2.  Выполните на распространителе в базе данных распространителя, [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), указав значение `replmonitor` для **@rolename** параметра. Если пользователь указан в `MemberName` в результирующем наборе, он уже принадлежит этой роли.  
  
3.  Если пользователь не принадлежит `replmonitor` роль, выполните [sp_addrolemember &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) на распространителе в базе данных распространителя. Укажите значение `replmonitor` для **@rolename** и имя пользователя базы данных или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows login being added для **@membername** .  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a>Удаление пользователя из предопределенной роли «replmonitor» базы данных  
  
1.  Чтобы убедиться, что пользователь принадлежит к `replmonitor` роль, выполните [sp_helprolemember &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) на распространителе в базе данных распространителя и укажите значение `replmonitor` для **@rolename** . Если пользователь не указан в поле `MemberName` результирующего набора, в данный момент он не принадлежит этой роли.  
  
2.  Если пользователь принадлежит к `replmonitor` роль, выполните [sp_droprolemember &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) на распространителе в базе данных распространителя. Укажите значение `replmonitor` для **@rolename** и имя пользователя базы данных или имя входа Windows, подлежащее удалению, для **@membername** .  
  
  
