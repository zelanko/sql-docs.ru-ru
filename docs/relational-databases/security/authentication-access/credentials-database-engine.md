---
title: "Учетные данные (компонент Database Engine) | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "субъекты [SQL Server], учетные данные"
  - "схемы [SQL Server], учетные данные"
  - "разрешения [SQL Server], учетные данные"
  - "группы [SQL Server], учетные данные"
  - "разрешение ALTER ANY CREDENTIAL"
  - "безопасность [SQL Server], учетные данные"
  - "проверка подлинности [SQL Server], учетные данные"
  - "пользователи [SQL Server], учетные данные"
  - "учетные данные [SQL Server], об учетных данных"
  - "учетные данные [SQL Server]"
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Учетные данные (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  Учетные данные представляют собой запись, которая содержит сведения для проверки подлинности (учетные данные), которые необходимы для подключения к ресурсу вне [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эти сведения используются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Большинство учетных данных содержат имя пользователя Windows и пароль.  
  
 Хранимые в учетных данных сведения позволяют пользователю, подключившемуся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с применением проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], обращаться к ресурсам, размещенным вне данного экземпляра сервера. Когда внешним ресурсом является ОС Windows, проверяется соответствие данных пользователя сведениям, указанным в учетной записи Windows. Одни учетные данные могут соответствовать нескольким зарегистрированным именам входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Но имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может соответствовать только одним учетным данным.  
  
 Сведения об учетных данных, которые хранятся в базе данных master и могут использоваться для всего экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], см. в разделе [CREATE CREDENTIAL (Transact-SQL)](../../../t-sql/statements/create-credential-transact-sql.md). Сведения об учетных данных, которые используются определенной базой данных и переносятся вместе с ней, см. в разделе [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
  
 Системные учетные данные создаются автоматически и связываются с определенными конечными точками. Имена для системных учетных данных начинаются с двух символов решетки (##).  
  
 Дополнительные сведения об учетных данных см. в представлениях каталога [sys.credentials](../../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) и [sys.database_credentials (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-credentials-transact-sql.md).  
  
## См. также  
 [Создание учетных данных](../../../relational-databases/security/authentication-access/create-a-credential.md) [CREATE CREDENTIAL (Transact-SQL)](../../../t-sql/statements/create-credential-transact-sql.md) [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
  
 [Обеспечение безопасности SQL Server](../../../relational-databases/security/securing-sql-server.md)  
  
  