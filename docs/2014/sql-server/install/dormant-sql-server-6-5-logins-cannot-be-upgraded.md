---
title: Невозможно обновить неактивные имена входа SQL Server 6.5 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 03cfdc1e7c639c387e175829f34329344fd9e160
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227184"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Невозможно обновить неактивные имена входа SQL Server 6.5
  Советник по переходу обнаружил имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], пароль которого нельзя напрямую обновить до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Чтобы активировать имя входа, необходимо сбросить его пароль. Можно изменить пароль с помощью инструкции ALTER LOGIN.  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 Новый пароль будет проверен на соответствие политике сложности паролей системы, если проверка политики не отключена. Рекомендуется использовать сложные пароли и не отключать политику проверки. Параметр MUST_CHANGE принуждает пользователя выбрать новый пароль. Это не обязательно, но рекомендуется.  
  
 Можно определить неактивные имена входа с помощью следующего запроса:  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
