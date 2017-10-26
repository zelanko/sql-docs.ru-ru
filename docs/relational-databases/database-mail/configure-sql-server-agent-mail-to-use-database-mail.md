---
title: "Настройка почты агента SQL Server на использование компонента Database Mail | Документация Майкрософт"
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fd14545a30d307845af1ce55be28334d4d8a25cc
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Настройка почты агента SQL Server на использование компонента Database Mail
  В этом разделе описывается настройка в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использования компонента Database Mail для отправки уведомлений и предупреждений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  Сведения о включении и настройке компонента Database Mail см. в разделе [Настройка компонента Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  Пример использования [!INCLUDE[tsql](../../includes/tsql-md.md)]см. в разделе [Создание профиля компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-profile.md).
  
-   **Перед началом работы выполните следующие действия.**  
  
-   [Предварительные требования](#Prerequisites)  
  
-   [Безопасность](#Security)  
  
-   [Настройка агента SQL Server на использование компонента Database Mail с помощью среды SQL Server Management Studio](#SSMSProcedure)  
  
-   [Задачи дополнительной работы](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   [Включить компонент Database Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Создать учетную запись компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md) для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [Создать профиль компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-profile.md) для учетной записи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы сделать пользователя членом роли **DatabaseMailUserRole** в базе данных **msdb** .  
  
-   Сделать профиль используемым по умолчанию в базе данных **msdb** .  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
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
  
-   [Предупреждения](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef)  
  
     Предупреждения могут быть настроены на уведомление оператора о возникновении в базе данных определенного события или о формировании в операционной системе определенных условий.  
  
-   [Операторы](http://msdn.microsoft.com/library/38e8488f-2669-4cea-b9c3-5f394a663678)  
  
     Операторы — это псевдонимы для людей или групп, которые могут получать электронные уведомления.  
  
  

