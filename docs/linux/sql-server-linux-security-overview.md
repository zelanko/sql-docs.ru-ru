---
title: "Ограничения безопасности для SQL Server для Linux | Документы Microsoft"
description: "В этом разделе описывает Linux ограничения SQL Server."
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 74357e2741e01e44f0f9d504456fca10f29f78e7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="security-limitations-for-sql-server-on-linux"></a>Ограничения безопасности для SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

SQL Server в Linux в настоящее время имеет следующие ограничения:

* Предоставляется стандартная пароля. Параметр MUST_CHANGE имеет единственный параметр, который можно настроить.  
* Расширенное управление ключами не поддерживается. 
* Использование ключей, хранящихся в хранилище ключей Azure не поддерживается.
* SQL Server создает свой собственный самозаверяющий сертификат для шифрования соединения. В настоящее время SQL Server не должен содержать пользователя, предоставленный сертификат для SSL или TLS. 

Дополнительные сведения о функции безопасности, доступные в SQL Server см. в разделе [центр обеспечения безопасности для ядра СУБД SQL Server и базы данных SQL Azure](https://msdn.microsoft.com/library/bb510589.aspx).

## <a name="next-steps"></a>Следующие шаги

Для типовых задач безопасности в разделе [приступить к работе со средствами безопасности SQL Server в Linux](sql-server-linux-security-get-started.md).   
Скрипт для изменения TCP порт номер каталогов SQL Server и настроить флага трассировки или параметров сортировки см. в разделе [Настройка SQL Server в Linux с mssql conf](sql-server-linux-configure-mssql-conf.md).

