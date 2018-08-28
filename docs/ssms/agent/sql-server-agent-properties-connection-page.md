---
title: Свойства агента SQL Server (страница "Подключение") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4d833d790d6d5924e4def27210ea1407215096d6
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42774837"
---
# <a name="sql-server-agent-properties-connection-page"></a>Свойства агента SQL Server (страница «Соединение»)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница используется для просмотра и изменения настроек соединения службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Псевдоним локального сервера**  
Указывает псевдоним, который применяется для подключения к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если невозможно использовать параметры соединения для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, определите псевдоним для экземпляра и укажите здесь псевдоним.  
  
**Использовать проверку подлинности Windows**  
В качестве метода проверки подлинности, используемого для подключения к экземпляру [!INCLUDE[msCoName](../../includes/msconame_md.md)] , устанавливается проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается как учетная запись, под которой работает служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Использовать проверку подлинности SQL Server**  
В качестве метода проверки подлинности, используемого для подключения к экземпляру сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , устанавливается проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается для обратной совместимости. Для повышения безопасности, по возможности, используйте проверку подлинности Windows.  
  
**Имя входа**  
Указывается имя входа, используемое для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Пароль**  
Указывается пароль, используемый для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
