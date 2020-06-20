---
title: Настройка пользователя для создания заданий агента SQL Server и управления ими | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995493"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configure a User to Create and Manage SQL Server Agent Jobs
  В этом разделе описывается настройка пользователя для создания или выполнения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заданий агента.  
  
-   **Перед началом работы:**  [Безопасность](#Security)  
  
-   **Настройка пользователя для создания заданий агента SQL Server и управления ими с помощью следующих средств:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Чтобы настроить пользователя для создания или выполнения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заданий агента, необходимо сначала добавить существующее SQL Server имя входа или роль msdb в одну из следующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предопределенных ролей базы данных агента в базе данных msdb: SQLAgentUserRole, SQLAgentReaderRole или SQLAgentOperatorRole.  
  
 По умолчанию члены этих ролей базы данных могут создавать свои собственные шаги заданий, которые запускаются сами по себе. Если пользователи, не являющиеся администраторами, желают выполнить задания, которые выполняют другие типы шагов заданий, например пакеты [!INCLUDE[ssIS](../../includes/ssis-md.md)] , им необходимо будет получить доступ к учетной записи-посреднику. Все члены предопределенной роли сервера sysadmin имеют разрешения на создание, изменение и удаление учетных записей-посредников. Дополнительные сведения о разрешениях, связанных с этими предопределенными ролями баз данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе [Предопределенные роли базы данных агента SQL Server](sql-server-agent-fixed-database-roles.md).  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Дополнительные сведения см. в разделе [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Использование среды SQL Server Management Studio  
 **Добавление имени входа SQL или роли базы данных msdb к предопределенной роли базы данных агента SQL Server**  
  
1.  В **Обозревателе объектов**разверните сервер.  
  
2.  Разверните элемент **Безопасность**, а затем элемент **Имена входа**.  
  
3.  Щелкните правой кнопкой мыши имя входа, которое необходимо добавить к предопределенной роли базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и выберите пункт **Свойства**.  
  
4.  На странице **Сопоставление пользователей** диалогового окна **Свойства имени входа** выберите строку, содержащую `msdb` .  
  
5.  На вкладке **Членство в роли базы данных для: msdb**выберите соответствующую предопределенную роль базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Настройка учетной записи-посредника для создания и управления шагами заданий агента SQL Server**  
  
1.  В **Обозревателе объектов**разверните сервер.  
  
2.  Разверните узел **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши элемент **Учетные записи-посредники** и выберите пункт **Создать учетную запись-посредник**.  
  
4.  На вкладке **Общие** диалогового окна **Создание учетной записи-посредника** укажите имя учетной записи-посредника, имя входа и описание. Обратите внимание, на то, что прежде чем создавать учетную запись-посредник агента SQL Server, необходимо создать учетные данные. Дополнительные сведения о создании учетных данных см. в статьях [Создание учетных данных](../../relational-databases/security/authentication-access/create-a-credential.md) и [Создание учетных данных &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).  
  
5.  Проверьте соответствующие подсистемы для этой учетной записи-посредника.  
  
6.  На вкладке **Участники** добавьте или удалите имена входа или роли, чтобы предоставить или отменить доступ к учетной записи-посреднику.  
  
## <a name="see-also"></a>См. также:  
 [Обеспечение безопасности агента SQL Server](implement-sql-server-agent-security.md)  
  
  
