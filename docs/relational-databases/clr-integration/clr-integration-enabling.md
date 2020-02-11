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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
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
  
 Вы можете отключить интеграцию со средой CLR, задав для параметра **clr enabled** значение 0. При отключении интеграции со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прекращает выполнение всех определяемых пользователем подпрограмм CLR и выгружает все домены приложений. Этот параметр не влияет на функции, зависящие от **** среды CLR, например тип `FORMAT` данных hierarchyid, функцию, репликацию и управление на основе политик, и будет продолжать функционировать.
  
> [!NOTE]  
>  Чтобы включить интеграцию со средой CLR, необходимо иметь разрешение ALTER SETTINGS на уровне сервера, которое неявно удерживается членами предопределенных ролей сервера **sysadmin** и **serveradmin** .  
  
> [!NOTE]  
>  Компьютеры, сконфигурированные для работы с большим объемом памяти и большим числом процессоров, при запуске сервера могут отказаться загружать функцию интеграции со средой CLR SQL Server. Чтобы устранить эту неполадку, запустите сервер с помощью параметра запуска службы **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и укажите достаточно большое значение памяти. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Перед включением интеграции со средой CLR необходимо отключить функцию использования упрощенных пулов. Дополнительные сведения см. в разделе [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>См. также:  
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «CLR Enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [ПРЕДОСТАВЛЕНИЕ &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
