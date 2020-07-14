---
title: Разработка приложений с помощью Always Encrypted | Документация Майкрософт
description: Узнайте о технологии шифрования на стороне клиента Always Encrypted, благодаря которой конфиденциальные данные никогда не будут раскрыты SQL Server или базе данных SQL Azure.
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6f348cf050941a06b2e0be6c37993a7f7458cb6a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85627567"
---
# <a name="develop-applications-using-always-encrypted"></a>Разработка приложений с помощью Always Encrypted
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) — это технология шифрования на стороне клиента, благодаря которой важные данные (и связанные с ними ключи шифрования) никогда не становятся доступны базе данных SQL Server или Azure SQL. При использовании Always Encrypted драйвер клиента прозрачно шифрует важные данные перед их передачей компоненту Database Engine, а также прозрачно расшифровывает данные, получаемые из зашифрованных столбцов базы данных.

Подробные сведения о разработке приложений, в которых используются базы данных, защищенные с помощью технологии Always Encrypted, и о том, какие драйверы клиентов и версии драйверов поддерживают Always Encrypted, см. в следующем разделе:

- [Using Always Encrypted with the .NET Framework Data Provider for SQL Server (Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server)](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Использование функции Always Encrypted с драйвером JDBC](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Использование функции Always Encrypted с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Использование функции Always Encrypted с драйверами PHP](../../../connect/php/using-always-encrypted-php-drivers.md)
- [Использование Always Encrypted поставщика данных Microsoft .NET для SQL Server в приложениях .NET Core и .NET Framework](../../../connect/ado-net/sql/sqlclient-support-always-encrypted.md)
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
