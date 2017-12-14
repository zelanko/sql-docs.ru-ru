---
title: "Свойства агента SQL Server (страница \"Подключение\") | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e8f11a99a7428200718b8fdf79aff9418d74bf32
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-properties-connection-page"></a>Свойства агента SQL Server (страница «Соединение»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Эта страница используется для просмотра и изменения настроек соединения службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Параметры  
**Псевдоним локального сервера**  
Указывает псевдоним, который применяется для подключения к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Если невозможно использовать параметры соединения для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] по умолчанию, определите псевдоним для экземпляра и укажите здесь псевдоним.  
  
**Использовать проверку подлинности Windows**  
В качестве метода проверки подлинности, используемого для подключения к экземпляру [!INCLUDE[msCoName](../../includes/msconame_md.md)] , устанавливается проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] подключается как учетная запись, под которой работает служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Использовать проверку подлинности SQL Server**  
В качестве метода проверки подлинности, используемого для подключения к экземпляру сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , устанавливается проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] поддерживается для обратной совместимости. Для повышения безопасности, по возможности, используйте проверку подлинности Windows.  
  
**Имя входа**  
Указывается имя входа, используемое для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Пароль**  
Указывается пароль, используемый для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
