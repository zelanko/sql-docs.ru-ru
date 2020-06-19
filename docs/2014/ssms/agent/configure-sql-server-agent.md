---
title: Настройка агента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
ms.openlocfilehash: b598d661fb79548ad3ee632455d4a718be60ee73
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995613"
---
# <a name="configure-sql-server-agent"></a>Configure SQL Server Agent
  В этом разделе описывается задание некоторых параметров конфигурации для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Доступ к полному набору параметров конфигурации агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно получить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SMO) или хранимых процедур агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   [Настройка агента SQL Server](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Щелкните элемент **Агент SQL Server** в обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для администрирования заданий, операторов, оповещений и службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако с узлом агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в обозревателе объектов можно работать только при наличии соответствующего разрешения.  
  
-   В экземплярах отказоустойчивых кластеров не должен быть включен автоматический перезапуск службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
 Дополнительные сведения о разрешениях Windows, необходимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы агента, см. в разделе [Выбор учетной записи для службы агент SQL Server](select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent"></a>Настройка агента SQL Server  
  
1.  Нажмите кнопку **Пуск** и щелкните в меню **Пуск**  элемент **Панель управления**.  
  
2.  На панели управления выберите категорию **Система и безопасность**, щелкните элемент **Администрирование**, а затем выберите пункт **Локальная политика безопасности**.  
  
3.  В окне «Локальная политика безопасности» щелкните треугольник, чтобы развернуть папку **Локальные политики** , а затем щелкните папку **Назначение прав пользователя** .  
  
4.  Щелкните правой кнопкой мыши разрешение, которое нужно настроить для использования с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и выберите пункт **Свойства**.  
  
5.  В диалоговом окне свойств разрешения убедитесь, что указана учетная запись, с которой работает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если это не так, нажмите кнопку **Добавить пользователя или группу**, введите учетную запись, с которой работает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в диалоговом окне **Выбор пользователей, компьютеров, учетных записей служб или групп** , а затем нажмите кнопку **ОК**.  
  
6.  Повторите эту процедуру для каждого разрешения, которое нужно добавить для работы с агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По окончании нажмите кнопку **ОК**.  
  
  
