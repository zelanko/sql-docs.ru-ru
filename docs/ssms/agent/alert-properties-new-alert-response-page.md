---
title: Свойства предупреждения — создание предупреждения (страница "Ответ") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 0e003a23046e640860c3b6abfa6c26809dd956e2
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="alert-properties---new-alert-response-page"></a>Свойства предупреждения — создание предупреждения (страница "Ответ")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу для указания задания, которое необходимо выполнить, и для получения списка операторов, которые должны получать уведомления в ответ на предупреждение агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  

## <a name="options"></a>Параметры  
**Выполнить задание**  
Включает параметры **Список заданий**, **Создать задание** и **Просмотреть задание** .  
  
**Создать задание**  
Откройте диалоговое окно **Создать задание** . Эта кнопка недоступна, если не установлен флажок **Выполнить задание** .  
  
**Просмотреть задание**  
Просмотреть или изменить выбранное задание. Этот параметр недоступен, если не установлен флажок **Выполнить задание** .  
  
**Уведомить операторов**  
Включает элементы управления, которые используются для добавления, удаления и изменения операторов.  
  
**Список операторов**  
Перечисляет операторов, которые должны получать уведомления при появлении предупреждения. Чтобы указать метод уведомления, установите флажок **Электронная почта**, **Пейджер**или **Net send** , отображаемый после имени оператора. Этот параметр недоступен, если флажок **Уведомить операторов** не установлен.  
  
**Электронная почта**  
Использовать электронную почту, чтобы уведомить оператора.  
  
**Пейджер**  
Использовать адрес электронной почты пейджера, чтобы уведомить оператора.  
  
**Net send**  
Использовать команду **net send** , чтобы уведомить оператора.  
  
**Создать оператор**  
Отображает диалоговое окно **Создать оператора** , которое используется для создания новых операторов.  
  
**Просмотр оператора**  
Отображается диалоговое окно **Свойства** для текущего выбранного оператора. Свойства операторов можно просматривать и изменять в диалоговом окне **Свойства оператора** .  
  
## <a name="see-also"></a>См. также:  
[Предупреждения](../../ssms/agent/alerts.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
[Предупреждения](../../ssms/agent/alerts.md)  
[Edit an Alert](../../ssms/agent/edit-an-alert.md)  
[Delete an Alert](../../ssms/agent/delete-an-alert.md)  
  
