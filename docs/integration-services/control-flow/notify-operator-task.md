---
title: "Задача «Уведомление оператора» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fb791195dccb44add2d1b196e33e03d3a45d7049
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="notify-operator-task"></a>задача «Уведомление оператора»
  Задача «Уведомление оператора» отправляет сообщения уведомления операторам агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оператор агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является псевдонимом человека или группы, которые могут принимать электронные уведомления. Дополнительные сведения об операторах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Операторы](http://msdn.microsoft.com/library/38e8488f-2669-4cea-b9c3-5f394a663678).  
  
 Используя задачу "Уведомление оператора", пакет может оповестить одного или нескольких операторов по электронной почте, интернет-пейджеру или с помощью команды **net send**. Каждый оператор может быть оповещен отдельным способом. Например, OperatorA может быть извещен по электронной почте и интернет-пейджеру, а OperatorB — через интернет-пейджер и команду **net send**. Операторы, получающие уведомления при помощи этого задания, должны быть членами коллекции **OperatorNotify** задачи «Уведомление оператора».  
  
 Задача «Уведомление оператора» является единственной задачей обслуживания базы данных, которая не содержит инструкции Transact-SQL или команды DBCC.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Настройка задачи «Уведомление оператора»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача уведомления оператора (план обслуживания)](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
