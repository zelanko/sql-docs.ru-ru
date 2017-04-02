---
title: "Постоянное шифрование (разработка клиентских приложений) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: 33
author: "stevestein"
manager: "jhubbard"
caps.handback.revision: 33
---
# Постоянное шифрование (разработка клиентских приложений)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) — это технология шифрования на стороне клиента, благодаря которой важные данные (и связанные с ними ключи шифрования) никогда не становятся доступны базе данных SQL Server или Azure SQL. При использовании Always Encrypted драйвер клиента прозрачно шифрует важные данные перед их передачей компоненту Database Engine, а также прозрачно расшифровывает данные, получаемые из зашифрованных столбцов базы данных.

Подробные сведения о разработке приложений, в которых используются базы данных, защищенные с помощью технологии Always Encrypted, и о том, какие драйверы клиентов и версии драйверов поддерживают Always Encrypted, см. в следующем разделе:

- [Using Always Encrypted with the .NET Framework Data Provider for SQL Server (Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server)](../../../relational-databases/security/encryption/develop using always encrypted with .net framework data provider.md)
- [Использование функции Always Encrypted с драйвером JDBC](https://msdn.microsoft.com/library/mt591987.aspx)
- [Использование постоянного шифрования с драйвером ODBC Windows](https://msdn.microsoft.com/library/mt637351.aspx)



## См. также:

[Always Encrypted (ядро СУБД)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
