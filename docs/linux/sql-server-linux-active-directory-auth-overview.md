---
title: Проверка подлинности Active Directory для SQL Server для Linux | Документы Microsoft
description: В этой статье обзор проверки подлинности Active Directory для SQL Server в Linux.
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 0d33fdbf0813eb8074743b47d36cdcf86af43d2c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Проверка подлинности Active Directory для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье содержится обзор проверки подлинности Active Directory (AD) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux. Проверки подлинности AD называется также встроенная проверка подлинности в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Обзор проверки подлинности AD

Проверка подлинности AD позволяет присоединенных к домену клиенты под управлением Windows или Linux, для проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью учетных данных домена, а протокол Kerberos.

Проверки подлинности AD имеет следующие преимущества по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] проверки подлинности:

- Пользователи проходят проверку подлинности через единый вход, не вводя пароль.   
- Создание имен входа для групп AD, можно управлять доступа и разрешений в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью членства в группах AD.  
- Каждый пользователь получает одно удостоверение во всей организации, поэтому не нужно для отслеживания которой [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] круг пользователей, которым соответствуют имена входа.   
- AD позволяет принудительно применять политику централизованного пароль во всей организации.   

## <a name="configuration-steps"></a>Шаги настройки

Для использования проверки подлинности Active Directory, контроллер домена AD (Windows) требуются в вашей сети.

В этом учебнике приведены подробные Настройка проверки подлинности AD [учебника: проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md). Ниже приведены сводные данные и ссылки на каждый раздел в учебнике.

1. [Присоединение к домену Active Directory узла SQL Server](sql-server-linux-active-directory-authentication.md#join).
1. [Создать пользователя AD для SQL Server и задайте параметру ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Настройка keytab службы SQL Server](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Создать имена входа SQL Server на основе AD в Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Подключение к SQL Server с использованием проверки подлинности AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Известные проблемы

- В настоящее время единственного способа проверки подлинности поддерживается для конечной точки зеркального отображения базы данных является СЕРТИФИКАТ. Метод проверки подлинности WINDOWS будет включена в будущем выпуске.
- AD сторонние средства, такие как Centrify Powerbroker, и Vintela не поддерживаются.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о том, как реализовать проверку подлинности Active Directory для SQL Server в Linux см. в разделе [учебника: проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).