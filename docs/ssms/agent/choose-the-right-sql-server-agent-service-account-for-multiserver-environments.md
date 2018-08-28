---
title: Выбор учетной записи службы агента для многосерверной среды | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d97f052c165bc3efb557c9c6b2e768804509ac4b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42774710"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Выбор правильной учетной записи службы агента SQL Server для многосерверной среды
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Данные учетной записи Windows, выбранной для службы «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], агент», могут повлиять на поведение многосерверного окружения следующим образом.  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» под учетной записью, не являющейся элементом локальной группы администраторов в Windows, прикрепление целевых серверов к главным серверам может завершиться сбоем. Если такой сбой произошел, выводится следующее сообщение об ошибке:  
  
    «Сбой операции прикрепления».  
  
    Для решения данной проблемы перезапустите службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент».  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» под локальной учетной записью операции между целевым и главными серверами осуществляются только при условии, что оба сервера находятся на одном компьютере. В случае использования такой конфигурации при прикреплении целевых серверов к главному серверу выводится следующее сообщение:  
  
    "Убедитесь, что стартовая учетная запись агента для *<имя_компьютера_целевого_сервера>* имеет права для входа на сервер targetServer".  
  
    Данное сообщение можно пропустить. Операция прикрепления должна быть завершена успешно.  
  
Дополнительные сведения о выборе учетной записи для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
