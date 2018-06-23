---
title: Включение интеграции со средой CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15ad6087fc711de1ab818b10d591cd48512bb9a3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188255"
---
# <a name="enabling-clr-integration"></a>Включение интеграции со средой CLR
  Функция интеграции со средой CLR отключена по умолчанию, поэтому ее нужно включить, чтобы использовать объекты, использующие интеграцию со средой CLR. Чтобы включить интеграцию со средой CLR, используйте **включена среда clr** параметр **sp_configure** хранимой процедуры:  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 Интеграция со средой CLR можно отключить, установив **включена среда clr** значение 0. При отключении интеграции со средой CLR [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] прекращает выполнение всех подпрограмм CLR и выгружает все домены приложений.  
  
> [!NOTE]  
>  Чтобы включить интеграцию со средой CLR, необходимо иметь разрешение ALTER SETTINGS на сервере уровня, которое неявно предоставляется членам **sysadmin** и **serveradmin** предопределенных ролей сервера.  
  
> [!NOTE]  
>  Компьютеры, сконфигурированные для работы с большим объемом памяти и большим числом процессоров, при запуске сервера могут отказаться загружать функцию интеграции со средой CLR SQL Server. Чтобы устранить эту проблему, запустите сервер с помощью **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] параметра запуска и укажите достаточно большое значение объема памяти. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Перед включением интеграции со средой CLR необходимо отключить функцию использования упрощенных пулов. Дополнительные сведения см. в разделе [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>См. также  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)   
 [Роли уровня сервера](../security/authentication-access/server-level-roles.md)  
  
  
