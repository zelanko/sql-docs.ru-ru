---
title: Настройка почты агента SQL Server на использование компонента Database Mail
ms.custom: seo-dt-2019
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0692421ca7e63b419c99ecc835516af4cbd5af0
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095777"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Настройка почты агента SQL Server на использование компонента Database Mail
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается настройка в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использования компонента Database Mail для отправки уведомлений и предупреждений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Сведения о включении и настройке компонента Database Mail см. в разделе [Настройка компонента Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  Пример использования [!INCLUDE[tsql](../../includes/tsql-md.md)]см. в разделе [Создание профиля компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-profile.md).
  
-   **Перед началом работы**  
  
-   [Предварительные требования](#Prerequisites)  
  
-   [безопасность](#Security)  
  
-   [Настройка агента SQL Server на использование компонента Database Mail с помощью среды SQL Server Management Studio](#SSMSProcedure)  
  
-   [Задачи дополнительной работы](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
  > [!NOTE]
  > Агент SQL в Управляемом экземпляре всегда настроен для использования компонента Database Mail, поэтому это содержимое неприменимо к Управляемому экземпляру. В Управляемом экземпляре должен быть профиль с именем **[AzureManagedInstance_dbmail_profile](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)** для привязки агента SQL Server к Database Mail. 
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   [Включить компонент Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Создать учетную запись компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md) для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [Создать профиль компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-profile.md) для учетной записи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы сделать пользователя членом роли **DatabaseMailUserRole** в базе данных **msdb** .
  
-   Сделать профиль используемым по умолчанию в базе данных **msdb** .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Пользователь, создающий учетные записи профилей и выполняющий хранимые процедуры, должен быть членом предопределенной роли сервера sysadmin.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Настройка агента SQL Server на использование компонента Database Mail**  
  
-   Разверните экземпляр сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в обозревателе объектов.  
  
-   Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
-   Нажмите **Система предупреждений**.  
  
-   Выберите **Включить почтовый профиль**.  
  
-   В списке **Почтовая система** выберите **Компонент Database Mail**.  
  
-   В **Списке почтовых профилей**выберите почтовый профиль для компонента Database Mail. 
  
-   Перезапустите агент SQL Server.  
  
##  <a name="Follow_Up"></a> Задачи дополнительной работы  
 Следующие задачи необходимо выполнить для завершения конфигурации агента на отправку предупреждений и уведомлений.  
  
-   [Предупреждения](../../ssms/agent/alerts.md)  
  
     Предупреждения могут быть настроены на уведомление оператора о возникновении в базе данных определенного события или о формировании в операционной системе определенных условий.  
  
-   [Операторы](../../ssms/agent/operators.md)  
  
     Операторы — это псевдонимы для людей или групп, которые могут получать электронные уведомления.  
  
  
