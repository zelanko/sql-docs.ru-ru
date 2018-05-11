---
title: Настройка аудита входа в систему (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2adb4b06480baf0411f8564a2de4815624cf470
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Настройка аудита входа в систему (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
В этом разделе описывается, как настроить аудит входа в [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)] для контроля подключения к компоненту [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]. Аудит входа в систему может быть настроен на запись в журнал ошибок при следующих событиях.  
  
-   Неуспешные входы в систему  
  
-   Успешные входы в систему  
  
-   Все попытки входа  
  
Чтобы этот параметр вступил в силу, перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Настройка аудита входа в систему  
  
1.  В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] с помощью обозревателя объектов.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Свойства**.  
  
3.  На странице **Безопасность** щелкните желаемый параметр под аудитом **Имя входа** и закройте страницу **Свойства сервера** .  
  
4.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Перезапустить**.  
  
