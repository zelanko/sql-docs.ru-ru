---
title: Задача "Уведомление оператора" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.notifyoperatortask.f1
helpviewer_keywords:
- Notify Operator task
- notifications [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30f1707c8d326942d2247bd3bcab31cdc38ab133
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294044"
---
# <a name="notify-operator-task"></a>задача «Уведомление оператора»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Задача «Уведомление оператора» отправляет сообщения уведомления операторам агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Оператор агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является псевдонимом человека или группы, которые могут принимать электронные уведомления. Дополнительные сведения об операторах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Операторы](../../ssms/agent/operators.md).  
  
 Используя задачу "Уведомление оператора", пакет может оповестить одного или нескольких операторов по электронной почте, интернет-пейджеру или с помощью команды **net send**. Каждый оператор может быть оповещен отдельным способом. Например, OperatorA может быть извещен по электронной почте и интернет-пейджеру, а OperatorB — через интернет-пейджер и команду **net send**. Операторы, получающие уведомления при помощи этого задания, должны быть членами коллекции **OperatorNotify** задачи «Уведомление оператора».  
  
 Задача «Уведомление оператора» является единственной задачей обслуживания базы данных, которая не содержит инструкции Transact-SQL или команды DBCC.  
  
## <a name="configuration-of-the-notify-operator-task"></a>Настройка задачи «Уведомление оператора»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача уведомления оператора (план обслуживания)](../../relational-databases/maintenance-plans/notify-operator-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
