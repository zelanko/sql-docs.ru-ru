---
title: "Параметр конфигурации сервера \"Agent XPs\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4635b2b686a706c5e7ca7454151828d885b8a61d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="agent-xps-server-configuration-option"></a>Параметр конфигурации сервера «Agent XPs»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используйте параметр **Agent XPs** , чтобы включить расширенные хранимые процедуры агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на этом сервере. Если этот параметр отключен, узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] недоступен в обозревателе объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 При использовании среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для запуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] эти расширенные хранимые процедуры включаются автоматически. Дополнительные сведения см. в разделе [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] В обозревателе объектов среды содержимое узла агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается до тех пор, пока эти расширенные хранимые процедуры не будут включены, вне зависимости от состояния службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Возможные значения:  
  
-   **0**, является признаком того, что расширенные хранимые процедуры агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] недоступны (по умолчанию).  
  
-   **1**, является признаком того, что расширенные хранимые процедуры агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны.  
  
 Новые настройки вступают в силу сразу же, без остановки или перезапуска сервера.  
  
## <a name="example"></a>Пример
 В следующем примере включаются расширенные хранимые процедуры агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

1. Откройте среду Microsoft SQL Server Management Studio и подключитесь к ядру СУБД.

2.  На панели "Стандартная" щелкните **Создать запрос**.

3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. 
  
```tsql 
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Задачи автоматизированного администрирования (агент SQL Server)](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Запуск, остановка или приостановка службы агента SQL Server](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  
