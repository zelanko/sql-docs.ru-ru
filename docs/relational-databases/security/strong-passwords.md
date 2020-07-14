---
title: Надежные пароли | Документация Майкрософт
description: Сведения о паролях в SQL Server и том, что представляет собой надежный пароль, помогающий повысить безопасность развертывания.
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
ms.openlocfilehash: ac636ae2b994b359921e164fe884de80a7d3486a
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001040"
---
# <a name="strong-passwords"></a>Надежные пароли
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Пароли могут быть самым слабым звеном в развертывании системы безопасности сервера. При выборе пароля всегда следует проявлять особую внимательность. Надежный пароль имеет следующие характеристики:  
  
-   содержит не менее восьми символов;  
  
-   сочетает в себе буквы, числа и специальные символы;  
  
-   не содержится в словарях;  
  
-   не является именем команды;  
  
-   не является именем человека;  
  
-   не является именем пользователя;  
  
-   не является именем компьютера;  
  
-   регулярно меняется;  
  
-   отличается от предыдущих паролей.  
  
 Пароли [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут содержать до 128 символов, включая буквы, знаки и цифры. Поскольку имена входа, имена пользователей, роли и пароли часто используются в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , определенные символы должны заключаться в двойные кавычки (") или квадратные скобки ([ ]). Используйте разделители в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , если имя входа, пользователь, роль или пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеют следующие характеристики:  
  
-   содержат пробел или начинаются с пробела;  
  
-   начинаются с символа $ или \@.  
  
 При использовании в строке подключения OLE DB или ODBC имя входа или пароль не должны содержать следующие символы: [] () , ; ? * ! \@ =. Эти символы используются для инициализации соединения или для указания его отдельных значений.  
  
## <a name="related-content"></a>См. также  
 [Политика паролей](../../relational-databases/security/password-policy.md)  
  
  
