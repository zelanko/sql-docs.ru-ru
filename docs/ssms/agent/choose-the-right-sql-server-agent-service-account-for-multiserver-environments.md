---
description: Выбор правильной учетной записи службы агента SQL Server для многосерверной среды
title: Выбор учетной записи службы агента для многосерверных сред
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 41a655bef2483f795a57ae6934fa768ad476d83c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88371890"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Выбор правильной учетной записи службы агента SQL Server для многосерверной среды

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Данные учетной записи Windows, выбранной для службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент», могут повлиять на поведение многосерверного окружения следующим образом.  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» под учетной записью, не являющейся элементом локальной группы администраторов в Windows, прикрепление целевых серверов к главным серверам может завершиться сбоем. Если такой сбой произошел, выводится следующее сообщение об ошибке:  
  
    «Сбой операции прикрепления».  
  
    Для решения данной проблемы перезапустите службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент».  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» под локальной учетной записью операции между целевым и главными серверами осуществляются только при условии, что оба сервера находятся на одном компьютере. В случае использования такой конфигурации при прикреплении целевых серверов к главному серверу выводится следующее сообщение:  
  
    "Убедитесь, что стартовая учетная запись агента для *<имя_компьютера_целевого_сервера>* имеет права для входа на сервер targetServer".  
  
    Данное сообщение можно пропустить. Операция прикрепления должна быть завершена успешно.  
  
Дополнительные сведения о выборе учетной записи для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
