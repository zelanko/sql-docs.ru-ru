---
title: Назначение сервера (SQL Server Management Studio) пересылки событий | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b14206560b5dd7a7feb0dd10901cbe7c58994c7e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097407"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Назначение сервера для перенаправления событий (SQL Server Management Studio)
  В этом разделе описано, как назначить сервер, на который [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенаправляет события в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Обратите внимание, что пересылка событий применяется к событиям между серверами, а не к событиям между экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , размещенными на одном компьютере. Также заметьте, что для получения перенаправленных событий сервер управления предупреждениями должен быть назначен экземпляром SQL Server по умолчанию.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Назначение сервера перенаправления событий с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо членство в предопределенной роли сервера **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>Назначение сервера пересылки событий  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, с которого требуется перенаправлять события на другой сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Свойства агента SQL —***имя_сервера* в разделе **Выберите страницу** выберите **Дополнительно**.  
  
4.  В области **Пересылка событий SQL Server**установите флажок **Перенаправить события на другой сервер** .  
  
5.  В списке **Сервер** выберите сервер, а затем на вкладке **События**выполните одно из следующих действий:  
  
    -   Выберите **Необработанные события** , чтобы выполнялась переадресация только событий, не обработанных локальными предупреждениями.  
  
    -   Выберите пункт **Все события** , чтобы выполнялась переадресация всех событий вне зависимости от того, обрабатывались они локальными предупреждениями или нет.  
  
6.  В списке **Если серьезность события равна или превышает** выберите степень серьезности, при которой события переадресуются выбранному серверу.  
  
7.  После завершения нажмите кнопку **ОК**.  
  
  