---
title: Надежные пароли | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6737a954881a56961b77dcf7d8f0373b0e30e848
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74564754"
---
# <a name="strong-passwords"></a>Надежные пароли
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
 Пароли [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать до 128 символов, включая буквы, знаки и цифры. Поскольку имена входа, имена пользователей, роли и пароли часто используются в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , определенные символы должны заключаться в двойные кавычки (") или квадратные скобки ([ ]). Используйте разделители в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , если имя входа, пользователь, роль или пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеют следующие характеристики:  
  
-   содержат пробел или начинаются с пробела;  
  
-   начинаются с символа $ или \@.  
  
 При использовании в строке подключения OLE DB или ODBC имя входа или пароль не должны содержать следующие символы: [] {} () , ; ? * ! \@ =. Эти символы используются для инициализации соединения или для указания его отдельных значений.  
  
## <a name="related-content"></a>См. также  
 [Политика паролей](../../relational-databases/security/password-policy.md)  
  
  
