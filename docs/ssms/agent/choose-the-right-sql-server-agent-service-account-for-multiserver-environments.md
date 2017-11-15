---
title: "Выбор учетной записи службы агента для многосерверной среды | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 78cf703b060e870e7fb8ee71152e95dd47239321
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Выбор правильной учетной записи службы агента SQL Server для многосерверной среды
Данные учетной записи Windows, выбранной для службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , агент», могут повлиять на поведение многосерверного окружения следующим образом.  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , агент» под учетной записью, не являющейся элементом локальной группы администраторов в Windows, прикрепление целевых серверов к главным серверам может завершиться сбоем. Если такой сбой произошел, выводится следующее сообщение об ошибке:  
  
    «Сбой операции прикрепления».  
  
    Для решения данной проблемы перезапустите службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и « [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , агент».  
  
-   При работе службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , агент» под локальной учетной записью операции между целевым и главными серверами осуществляются только при условии, что оба сервера находятся на одном компьютере. В случае использования такой конфигурации при прикреплении целевых серверов к главному серверу выводится следующее сообщение:  
  
    "Убедитесь, что стартовая учетная запись агента для *<имя_компьютера_целевого_сервера>* имеет права для входа на сервер targetServer".  
  
    Данное сообщение можно пропустить. Операция прикрепления должна быть завершена успешно.  
  
Дополнительные сведения о выборе учетной записи для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] см. в разделе [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
