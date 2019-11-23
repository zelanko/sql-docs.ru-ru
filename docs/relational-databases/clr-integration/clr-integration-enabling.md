---
title: Включение интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 09/17/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 07066dc7ffbd48273ace55e0c9867661b2cbfe59
ms.sourcegitcommit: 445842da7c7d216b94a9576e382164c67f54e19a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2019
ms.locfileid: "71680851"
---
# <a name="clr-integration---enabling"></a>Включение интеграции со средой CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Функция интеграции со средой CLR отключена по умолчанию, поэтому ее нужно включить, чтобы использовать объекты, использующие интеграцию со средой CLR. Чтобы включить интеграцию со средой CLR, используйте параметр **clr enabled** хранимой процедуры **sp_configure** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
EXEC sp_configure 'clr enabled', 1;  
RECONFIGURE;  
GO  
```  
  
 Вы можете отключить интеграцию со средой CLR, задав для параметра **clr enabled** значение 0. При отключении интеграции со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прекращает выполнение всех пользовательских подпрограмм CLR и выгружает все домены приложений. На функции, зависящие от среды CLR, такие как тип данных **hierarchyid** , функция `FORMAT`, репликация и управление на основе политик, не затрагиваются этим параметром и будут продолжать функционировать.
  
> [!NOTE]  
>  Чтобы включить интеграцию со средой CLR, необходимо иметь разрешение ALTER SETTINGS на уровне сервера, которое неявно удерживается членами предопределенных ролей сервера **sysadmin** и **serveradmin** .  
  
> [!NOTE]  
>  Компьютеры, сконфигурированные для работы с большим объемом памяти и большим числом процессоров, при запуске сервера могут отказаться загружать функцию интеграции со средой CLR SQL Server. Чтобы устранить эту неполадку, запустите сервер с помощью параметра запуска службы[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-gmemory_to_reserve** и укажите достаточно большое значение памяти. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Перед включением интеграции со средой CLR необходимо отключить функцию использования упрощенных пулов. Дополнительные сведения см. в разделе [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>См. также статью  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
