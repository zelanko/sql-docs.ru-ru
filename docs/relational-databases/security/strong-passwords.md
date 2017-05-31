---
title: "Надежные пароли | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e58e590b2b57c96a18b8752b33d7b559b375d028
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="strong-passwords"></a>Надежные пароли
  Пароли могут быть самым слабым звеном в развертывании системы безопасности сервера. При выборе пароля всегда следует проявлять особую внимательность. Надежный пароль имеет следующие характеристики:  
  
-   содержит как минимум 8 символов;  
  
-   сочетает в себе буквы, числа и специальные символы;  
  
-   не содержится в словарях;  
  
-   не является именем команды;  
  
-   не является именем человека;  
  
-   не является именем пользователя;  
  
-   не является именем компьютера;  
  
-   регулярно меняется;  
  
-   в значительной степени отличается от предыдущих паролей.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать до 128 символов, включая буквы, знаки и цифры. Поскольку имена входа, имена пользователей, роли и пароли часто используются в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , определенные символы должны заключаться в двойные кавычки (") или квадратные скобки ([ ]). Используйте разделители в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , если имя входа, пользователь, роль или пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеют следующие характеристики:  
  
-   содержат пробел или начинаются с пробела;  
  
-   начинаются с символа $ или @.  
  
 При использовании в строке подключения OLE DB или ODBC имя входа или пароль не должны содержать следующие символы: [] {}() , ; ? * ! @. Эти символы используются для инициализации соединения или для указания его отдельных значений.  
  
## <a name="related-content"></a>См. также  
 [Политика паролей](../../relational-databases/security/password-policy.md)  
  
  
