---
title: Выберите справа SQL Server учетная запись службы агента для многосерверной среды | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33b35dbf6a2ccbc99e881a344674cb59ecc4b330
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268110"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Выбор правильной учетной записи службы агента SQL Server для многосерверной среды
  Данные учетной записи Windows, выбранной для службы «[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], агент», могут повлиять на поведение многосерверного окружения следующим образом.  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» под учетной записью, не являющейся элементом локальной группы администраторов в Windows, прикрепление целевых серверов к главным серверам может завершиться сбоем. Если такой сбой произошел, выводится следующее сообщение об ошибке:  
  
     «Сбой операции прикрепления».  
  
     Для решения данной проблемы перезапустите службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент».  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» под локальной учетной записью операции между целевым и главными серверами осуществляются только при условии, что оба сервера находятся на одном компьютере. В случае использования такой конфигурации при прикреплении целевых серверов к главному серверу выводится следующее сообщение:  
  
     "Убедитесь, что стартовая учетная запись агента для *<имя_компьютера_целевого_сервера>* имеет права для входа на сервер targetServer".  
  
     Данное сообщение можно пропустить. Операция прикрепления должна быть завершена успешно.  
  
 Дополнительные сведения о выборе учетной записи для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Выбор учетной записи для службы агента SQL Server](select-an-account-for-the-sql-server-agent-service.md).  
  
  
