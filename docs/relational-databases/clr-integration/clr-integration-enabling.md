---
title: "Включение интеграции со средой CLR | Документы Microsoft"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 25ced29f577ca896f190922e7debfc82c1fcc6f4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="clr-integration---enabling"></a>Интеграция со средой CLR - Включение
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Компонент интеграции среды выполнения (CLR) по умолчанию и нужно включить, чтобы использовать объекты, использующие интеграцию со средой CLR. Чтобы включить интеграцию со средой CLR, используйте **включена среда clr** параметр **sp_configure** хранимой процедуры в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 Интеграция со средой CLR можно отключить, установив **включена среда clr** значение 0. При отключении интеграции со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прекращает выполнение всех подпрограмм CLR и выгружает все домены приложений.  
  
> [!NOTE]  
>  Чтобы включить интеграцию со средой CLR, необходимо иметь разрешение ALTER SETTINGS на сервере уровня, которое неявно предоставляется членам **sysadmin** и **serveradmin** предопределенных ролей сервера.  
  
> [!NOTE]  
>  Компьютеры, сконфигурированные для работы с большим объемом памяти и большим числом процессоров, при запуске сервера могут отказаться загружать функцию интеграции со средой CLR SQL Server. Чтобы устранить эту проблему, запустите сервер с помощью **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметра запуска и укажите достаточно большое значение объема памяти. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Перед включением интеграции со средой CLR необходимо отключить функцию использования упрощенных пулов. Дополнительные сведения см. в разделе [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>См. также:  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
