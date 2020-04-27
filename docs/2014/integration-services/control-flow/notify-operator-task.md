---
title: Задача "Уведомление оператора" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f2534aef1fedb2a7991c5d2e0341e46711cc7b55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62830418"
---
# <a name="notify-operator-task"></a>задача «Уведомление оператора»
  Задача «Уведомление оператора» отправляет сообщения уведомления операторам агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оператор агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является псевдонимом человека или группы, которые могут принимать электронные уведомления. Дополнительные сведения об операторах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Операторы](../../ssms/agent//operators.md).  
  
 Используя задачу "Уведомление оператора", пакет может оповестить одного или нескольких операторов по электронной почте, интернет-пейджеру или с помощью команды **net send**. Каждый оператор может быть оповещен отдельным способом. Например, OperatorA может быть извещен по электронной почте и интернет-пейджеру, а OperatorB — через интернет-пейджер и команду **net send**. Операторы, получающие уведомления при помощи этого задания, должны быть членами коллекции **OperatorNotify** задачи «Уведомление оператора».  
  
 Задача «Уведомление оператора» является единственной задачей обслуживания базы данных, которая не содержит инструкции Transact-SQL или команды DBCC.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Настройка задачи «Уведомление оператора»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача уведомления оператора (план обслуживания)](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
  
