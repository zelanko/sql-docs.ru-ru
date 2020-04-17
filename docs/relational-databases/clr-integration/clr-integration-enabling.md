---
title: Включение интеграции CLR (англ.) Документы Майкрософт
description: Хостинг CLR сервера Microsoft S'L называется интеграцией CLR, которая отключена по умолчанию. Используйте sp_configure сохраненную процедуру для обеспечения интеграции CLR.
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
ms.openlocfilehash: 7d161135c8c8b0c7d7932eb08aa98509efc4bc45
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488119"
---
# <a name="clr-integration---enabling"></a>Включение интеграции со средой CLR
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Функция интеграции со средой CLR отключена по умолчанию, поэтому ее нужно включить, чтобы использовать объекты, использующие интеграцию со средой CLR. Для обеспечения интеграции CLR используйте опцию **включенного clr** процедуры **sp_configure** сохранены в: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
```sql  
EXEC sp_configure 'clr enabled', 1;  
RECONFIGURE;  
GO  
```  
  
 Вы можете отключить интеграцию CLR, установив опцию **включенного clr** до 0. Когда вы отключите интеграцию CLR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перестанете исполнять все пользовательские процедуры CLR и разгружает все домены приложений. Функции, которые полагаются на CLR, такие как `FORMAT` тип данных **иерархии,** функция, репликация и управление на основе политики, не зависят от этого параметра и будут продолжать функционировать.
  
> [!NOTE]  
>  Для обеспечения интеграции CLR необходимо иметь разрешение на серверный уровень ALTER SETTINGS, которое неявно удерживается членами **sysadmin** и **sradradmin** фиксированными ролями сервера.  
  
> [!NOTE]  
>  Компьютеры, сконфигурированные для работы с большим объемом памяти и большим числом процессоров, при запуске сервера могут отказаться загружать функцию интеграции со средой CLR SQL Server. Чтобы решить эту проблему, запустите сервер с помощью опции запуска **службы -gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и укажите значение памяти достаточно большим. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Перед включением интеграции со средой CLR необходимо отключить функцию использования упрощенных пулов. Дополнительные сведения см. в разделе [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>См. также:  
 [sp_configure &#40;&#41;«Трансакт-СЗЛ»](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr включен вариант конфигурации сервера](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [&#41;RECONFIGURE &#40;"Трансакт-СЗЛ"](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [&#41;&#40;GRANT](../../t-sql/statements/grant-transact-sql.md)   
 [Роли уровня сервера](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
