---
title: Форматирование адресов пейджеров для предупреждений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83ece1b0392f303d10b7f431789c6829abb87bdf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256046"
---
# <a name="format-pager-addresses-for-alerts"></a>Форматирование адресов пейджеров для предупреждений
  В этом разделе описывается форматирование адресов пейджера для предупреждений агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для форматирования адресов пейджера используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 По умолчанию только члены предопределенной роли сервера **sysadmin** могут просматривать сведения о предупреждении. Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>Форматирование адресов пейджера  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий оповещение агента, которое необходимо отправить на пейджер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В разделе **Выбор страницы**выберите пункт **Система предупреждений**.  
  
4.  В полях **Кому** и **Копия** в поле **Форматирование адреса для электронных сообщений на пейджер** введите префикс или суффикс адресов пейджеров. При отправке уведомления подставляется действительный адрес пейджера оператора.  
  
5.  В поле **Тема** введите префикс или суффикс, добавляемый к строке темы.  
  
6.  Установите флажок **Включить тело сообщения электронной почты в сообщение уведомления** , чтобы в сообщение, отправляемое на пейджер, включался полный текст электронного сообщения (а не только строка темы).  
  
7.  После завершения нажмите кнопку **ОК**.  
  
  
