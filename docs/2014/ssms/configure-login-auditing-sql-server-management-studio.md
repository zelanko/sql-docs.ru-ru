---
title: Настройка аудита входа в систему (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4cede183f39ed7aca5bfe6bc7f0226c96da6ca84
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245659"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Настройка аудита входа в систему (среда SQL Server Management Studio)
  В этом разделе описывается, как настроить аудит входа в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] для контроля подключения к компоненту [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]. Аудит входа в систему может быть настроен на запись в журнал ошибок при следующих событиях.  
  
-   Неуспешные входы в систему  
  
-   Успешные входы в систему  
  
-   Все попытки входа  
  
 Чтобы этот параметр вступил в силу, перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Настройка аудита входа в систему  
  
1.  В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] с помощью обозревателя объектов.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Свойства**.  
  
3.  На странице **Безопасность** щелкните желаемый параметр под аудитом **Имя входа** и закройте страницу **Свойства сервера** .  
  
4.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Перезапустить**.  
  
  
