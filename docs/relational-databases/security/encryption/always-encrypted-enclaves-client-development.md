---
title: Разработка приложений с помощью Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 10/15/2019
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
ms.openlocfilehash: 54e282e7d68c23837c1865f1257ba7e159644d26
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73595539"
---
# <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>Разработка приложений с помощью Always Encrypted с безопасными анклавами
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

[Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) расширяет возможности [Always Encrypted](always-encrypted-database-engine.md) для реализации более широких возможностей запросов приложений к зашифрованным столбцам базы данных. Используемые технологии безопасных анклавов позволяют исполнителю запросов в [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] делегировать вычисления в зашифрованных столбцах безопасному анклаву внутри процесса [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)].

## <a name="client-driver-for-always-encrypted-with-secure-enclaves"></a>Драйвер клиента для Always Encrypted с безопасными анклавами

Для разработки приложений с помощью Always Encrypted с защищенными анклавами требуется версия драйвера клиента SQL, поддерживающая безопасные анклавы. Драйвер клиента играет следующую ключевую роль.
- Перед отправкой запроса, который использует безопасный анклав, в [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] для выполнения, драйвер инициирует аттестацию анклава для проверки его подлинности и безопасной работы для обработки конфиденциальных данных. Дополнительные сведения об аттестации см. в статье [Аттестация безопасного анклава](always-encrypted-enclaves.md#secure-enclave-attestation).
- После завершения аттестации драйвер клиента устанавливает защищенный сеанс с анклавом путем согласования общего секрета.
- Драйвер использует общий секрет для шифрования ключей шифрования столбцов, которые потребуются анклаву для обработки запроса, и отправляет ключи [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)], который пересылает их в безопасный анклав для расшифровки. 
- Наконец, драйвер отправляет запрос для выполнения, который активирует вычисления в безопасном анклаве.

Чтобы использовать функциональность безопасного анклава, необходимо настроить приложение и драйвер клиента для поддержки вычислений анклава при подключении к базе данных и указать конечную точку службы аттестации (URL-адрес аттестации анклава), указывающую на службу аттестации для анклава. Подробные настройки зависят от используемого драйвера и службы или протокола аттестации.

## <a name="next-steps"></a>Следующие шаги

Следующие драйверы клиента поддерживают Always Encrypted с безопасными анклавами.
- Поставщик данных .NET Framework для SQL Server в .NET Framework 4.7.2 и выше. 
    - Дополнительные сведения см. в статье [Использование Always Encrypted с поставщиком данных .NET Framework для SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md).
    - Пошаговое руководство см. в статье [Учебник. Разработка приложения .NET Framework с помощью Always Encrypted с безопасными анклавами](../tutorial-always-encrypted-enclaves-develop-net-framework-apps.md)
- Microsoft ODBC Driver for SQL Server версии 17.4 или выше. 
    - Дополнительные сведения см. в статье [Использование функции Always Encrypted с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md). 
    - Сведения о включении вычислений анклава для подключения к базе данных с помощью ODBC см. в статье [Включение Always Encrypted с безопасными анклавами](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves).
