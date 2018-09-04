---
title: Постоянное шифрование (разработка клиентских приложений) | Документация Майкрософт
ms.custom: ''
ms.date: 08/21/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c75bb08f0c96c386db8a9eee307e696b31c67160
ms.sourcegitcommit: 010755e6719d0cb89acb34d03c9511c608dd6c36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "43239792"
---
# <a name="always-encrypted-client-development"></a>Постоянное шифрование (разработка клиентских приложений)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) — это технология шифрования на стороне клиента, благодаря которой важные данные (и связанные с ними ключи шифрования) никогда не становятся доступны базе данных SQL Server или Azure SQL. При использовании Always Encrypted драйвер клиента прозрачно шифрует важные данные перед их передачей компоненту Database Engine, а также прозрачно расшифровывает данные, получаемые из зашифрованных столбцов базы данных.

Подробные сведения о разработке приложений, в которых используются базы данных, защищенные с помощью технологии Always Encrypted, и о том, какие драйверы клиентов и версии драйверов поддерживают Always Encrypted, см. в следующем разделе:

- [Using Always Encrypted with the .NET Framework Data Provider for SQL Server (Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server)](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Использование функции Always Encrypted с драйвером JDBC](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Использование функции Always Encrypted с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Использование функции Always Encrypted с драйверами PHP](../../../connect/php/using-always-encrypted-php-drivers.md)

> [!NOTE]
> Always Encrypted не поддерживается в настоящее время в [.NET CORE](https://docs.microsoft.com/dotnet/core/).

## <a name="see-also"></a>См. также:

[Always Encrypted (ядро СУБД)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

