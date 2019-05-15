---
title: Настройка аудита входа в систему (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], logins
- logins [SQL Server], auditing
ms.assetid: 16961116-57ac-4eef-8037-791b26ade548
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1ce5c0323d98e2b8f05813513b3a2f44444a6695
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65102783"
---
# <a name="configure-login-auditing-sql-server-management-studio"></a>Настройка аудита входа в систему (среда SQL Server Management Studio)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
В этом разделе описывается, как настроить аудит входа в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] для контроля подключения к компоненту [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)]. Аудит входа в систему может быть настроен на запись в журнал ошибок при следующих событиях.  
  
-   Неуспешные входы в систему  
  
-   Успешные входы в систему  
  
-   Все попытки входа  
  
Чтобы этот параметр вступил в силу, перезапустите [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-login-auditing"></a>Настройка аудита входа в систему  
  
1.  В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] с помощью обозревателя объектов.  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Свойства**.  
  
3.  На странице **Безопасность** щелкните желаемый параметр под аудитом **Имя входа** и закройте страницу **Свойства сервера** .  
  
4.  В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Перезапустить**.  
  
