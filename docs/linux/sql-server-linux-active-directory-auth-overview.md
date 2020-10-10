---
title: Проверка подлинности Azure Active Directory для SQL Server на Linux
titleSuffix: SQL Server
description: В этой статье приводятся общие сведения о проверке подлинности Active Directory для SQL Server на Linux.
ms.date: 04/01/2019
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: efce6c9f297c3dba58a37a3d097a9c8176efa287
ms.sourcegitcommit: b93beb4f03aee2c1971909cb1d15f79cd479a35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/29/2020
ms.locfileid: "91497995"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Проверка подлинности Azure Active Directory для SQL Server на Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

В этой статье приводятся общие сведения о проверке подлинности Active Directory (AD) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на Linux. Проверка подлинности AD в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] также называется встроенной проверкой подлинности.

## <a name="ad-authentication-overview"></a>Общие сведения о проверке подлинности AD

С помощью проверки подлинности AD присоединенные к домену клиенты с Windows или Linux могут проходить проверку подлинности в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], используя свои учетные данные домена и протокол Kerberos.

Проверка подлинности AD имеет следующие преимущества в сравнении с проверкой подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:

- Пользователи проходят проверку подлинности с помощью функции единого входа, не вводя пароль.
- Создавая имена входа для групп AD, вы можете управлять доступом и разрешениями в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на основе членства в группе AD.  
- Каждый пользователь имеет единое удостоверение на уровне организации, благодаря чему вам не нужно отслеживать, каким людям соответствуют различные имена входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].   
- AD позволяет применять централизованную политику управления паролями на уровне организации.

## <a name="configuration-steps"></a>Этапы настройки

Чтобы использовать проверку подлинности Active Directory, в вашей сети должен присутствовать контроллер домена AD (Windows).

Дополнительные сведения о настройке проверки подлинности приводятся в разделе [Руководство. Использование проверки подлинности Azure Active Directory с SQL Server на Linux](sql-server-linux-active-directory-authentication.md). В следующем списке приводятся общие сведения со ссылками на соответствующие разделы руководства:

1. [Присоединение узла SQL Server к домену Active Directory](sql-server-linux-active-directory-join-domain.md).
1. [Создание пользователя AD для SQL Server и настройка свойства ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Настройка KEYTAB-файла службы SQL Server](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Защита KEYTAB-файла](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Настройка SQL Server для использования KEYTAB-файла для проверки подлинности Kerberos](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Создание имен входа SQL Server на основе AD в Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Подключение к SQL Server с помощью проверки подлинности AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Известные проблемы

- На данный момент единственный поддерживаемый способ проверки подлинности для конечной точки с зеркальным отображением базы данных — CERTIFICATE. Способ проверки подлинности WINDOWS будет включен в последующем выпуске.
- SQL Server на Linux не поддерживает протокол NTLM для удаленных подключений. Локальное подключение может работать с NTLM.

## <a name="next-steps"></a>Next Steps

Дополнительные сведения о реализации проверки подлинности Active Directory для SQL Server на Linux см. в разделе [Руководство. Использование проверки подлинности Azure Active Directory с SQL Server на Linux](sql-server-linux-active-directory-authentication.md).
