---
title: Изменение режима проверки подлинности сервера
description: Сведения об изменении режима проверки подлинности сервера в SQL Server. Для этого вы можете использовать SQL Server Management Studio или Transact-SQL.
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: markingmyname
ms.author: maghan
ms.custom: ''
ms.date: 02/18/2020
ms.openlocfilehash: 79dc463039be1100f265e6bb44561a6e2dc71c93
ms.sourcegitcommit: bf5acef60627f77883249bcec4c502b0205300a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88200954"
---
# <a name="change-server-authentication-mode"></a>Изменение режима проверки подлинности сервера

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом разделе описывается, как изменить режим проверки подлинности сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. В процессе установки компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] настраивается на использование **режима проверки подлинности Windows** или **режима проверки подлинности SQL Server и Windows**. После установки вы можете изменить режим проверки подлинности в любое время.

Если во время установки был выбран **Режим проверки подлинности Windows** , то имя входа sa отключено, а пароль присваивается программой установки. Если впоследствии изменить режим проверки подлинности на **проверку подлинности SQL Server и Windows**, то имя входа sa останется отключенным. Чтобы можно было пользоваться именем входа sa, включите его и присвойте ему новый пароль с помощью инструкции ALTER LOGIN. Имя входа sa может подключаться к серверу только с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

## <a name="before-you-begin"></a>Перед началом

Учетная запись sa — хорошо известная учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и часто становится мишенью злоумышленников. Не включайте учетную запись sa, если это не требуется для работы приложения. Для имени входа sa очень важно использовать надежный пароль.

## <a name="change-authentication-mode-with-ssms"></a>Изменение режима проверки подлинности с помощью SSMS

1. В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.

2. На странице **Безопасность** , в разделе **Серверная проверка подлинности**выберите новый режим проверки подлинности сервера, а затем нажмите кнопку **ОК**.

3. В диалоговом окне среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] нажмите кнопку **ОК** , чтобы подтвердить необходимость перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

4. В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Перезапустить**. Если работает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , он тоже должен быть перезапущен.

## <a name="enable-sa-login"></a>Включение имени входа sa

Имя входа **sa** можно включить с помощью SSMS или T-SQL.

### <a name="use-ssms"></a>использование SSMS;

1. В обозревателе объектов разверните узел **Безопасность**, разверните "Имена входа", щелкните правой кнопкой мыши имя входа **sa**и выберите **Свойства**.

2. На вкладке **Общие**, возможно, придется создать и подтвердить пароль для имени входа **sa**.

3. На странице **Состояние** в разделе **Имя входа** щелкните **Включить**и нажмите кнопку **ОК**.

### <a name="using-transact-sql"></a>Использование Transact-SQL

В следующем примере включается имя входа sa и устанавливается новый пароль. Замените `<enterStrongPasswordHere>` надежным паролем.

```sql  
ALTER LOGIN sa ENABLE ;  
GO  
ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
GO  
```

## <a name="change-authentication-mode-t-sql"></a>Изменение режима проверки подлинности (T-SQL)

В следующем примере проверка подлинности сервера переключается со смешанного режима (Windows + SQL) на Windows.

> [!CAUTION]
> В следующем примере для изменения реестра сервера используется расширенная хранимая процедура. При неправильном изменении реестра могут возникнуть серьезные проблемы. В результате может потребоваться переустановка операционной системы. Корпорация Майкрософт не гарантирует, что эти проблемы можно устранить. Ответственность за изменение реестра лежит на пользователе.

```sql
USE [master]
GO
EXEC xp_instance_regwrite N'HKEY_LOCAL_MACHINE', 
     N'Software\Microsoft\MSSQLServer\MSSQLServer',
     N'LoginMode', REG_DWORD, 1
GO
```

> [!Note]
> Для изменения режима аутентификации необходимы разрешения [системного администратора](../../relational-databases/security/authentication-access/server-level-roles.md#fixed-server-level-roles) или [сервера контроля](../../relational-databases/security/permissions-database-engine.md)

## <a name="see-also"></a>См. также

- [Надежные пароли](../../relational-databases/security/strong-passwords.md)
- [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)
- [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)
- [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)
