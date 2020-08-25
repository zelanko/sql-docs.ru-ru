---
title: Ограничения системы безопасности для SQL Server на Linux
description: Сведения об ограничениях SQL Server на Linux, в том числе о том, что использование ключей, хранящихся в Azure Key Vault, и расширенное управление ключами не поддерживаются.
author: VanMSFT
ms.author: vanto
ms.date: 09/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 611afe6c02e979c7c9672d7d94f84844b8932cf6
ms.sourcegitcommit: 3ea082c778f6771b17d90fb597680ed334d3e0ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/11/2020
ms.locfileid: "88088807"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Ограничения системы безопасности для SQL Server на Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

SQL Server на Linux в настоящее время имеет указанные ниже ограничения.

* Применяется стандартная политика паролей. MUST_CHANGE — это единственный параметр, который можно настроить. Параметр CHECK_POLICY не поддерживается.
* Расширенное управление ключами не поддерживается. 
* Использование ключей, хранящихся в Azure Key Vault, не поддерживается.
* SQL Server создает собственный самозаверяющий сертификат для шифрования подключений. В SQL Server можно настроить использование предоставляемого пользователем сертификата для TLS. 

Дополнительные сведения о функциях безопасности, доступных в SQL Server, см. в статье [Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Дальнейшие действия

Описание стандартных задач по обеспечению безопасности см. в статье [Начало работы с функциями безопасности SQL Server на Linux](sql-server-linux-security-get-started.md). Скрипт для изменения номера TCP-порта и каталогов SQL Server, а также настройки флагов трассировки или параметров сортировки можно найти в статье [Настройка SQL Server в Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md).
