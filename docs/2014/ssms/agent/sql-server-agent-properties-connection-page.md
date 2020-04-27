---
title: Свойства агента SQL Server (страница "Подключение") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0c387513b8896018ead7d35e15a32e9e314ac0d3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63245730"
---
# <a name="sql-server-agent-properties-connection-page"></a>Свойства агента SQL Server (страница «Соединение»)
  Эта страница используется для просмотра и изменения параметров соединения от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы агента к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Псевдоним локального сервера**  
 Указывает псевдоним, который применяется для подключения к локальному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если невозможно использовать параметры соединения для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, определите псевдоним для экземпляра и укажите здесь псевдоним.  
  
 **Использовать проверку подлинности Windows**  
 В качестве метода проверки подлинности, используемого для подключения к экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] , устанавливается проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается как учетная запись, под которой работает служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Использовать проверку подлинности SQL Server**  
 В качестве метода проверки подлинности, используемого для подключения к экземпляру сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , устанавливается проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается для обратной совместимости. Для повышения безопасности, по возможности, используйте проверку подлинности Windows.  
  
 **Имя входа**  
 Указывается имя входа, используемое для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Пароль**  
 Указывается пароль, используемый для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
