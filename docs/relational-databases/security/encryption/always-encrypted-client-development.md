---
title: "Постоянное шифрование (разработка клиентских приложений) | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 07/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: "33"
author: stevestein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 103b3d51f8d9e1a5d809b9202a9808e8a5978bfe
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="always-encrypted-client-development"></a>Постоянное шифрование (разработка клиентских приложений)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) — это технология шифрования на стороне клиента, благодаря которой важные данные (и связанные с ними ключи шифрования) никогда не становятся доступны базе данных SQL Server или Azure SQL. При использовании Always Encrypted драйвер клиента прозрачно шифрует важные данные перед их передачей компоненту Database Engine, а также прозрачно расшифровывает данные, получаемые из зашифрованных столбцов базы данных.

Подробные сведения о разработке приложений, в которых используются базы данных, защищенные с помощью технологии Always Encrypted, и о том, какие драйверы клиентов и версии драйверов поддерживают Always Encrypted, см. в следующем разделе:

- [Using Always Encrypted with the .NET Framework Data Provider for SQL Server (Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server)](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Использование функции Always Encrypted с драйвером JDBC](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Использование постоянного шифрования с драйвером ODBC Windows](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)



## <a name="see-also"></a>См. также:

[Always Encrypted (ядро СУБД)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

