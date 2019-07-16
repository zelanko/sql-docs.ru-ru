---
title: Ограничения безопасности для SQL Server в Linux
description: В этой статье описывается SQL Server на Linux ограничения.
author: VanMSFT
ms.author: vanto
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9f54197c8613293b36c1eb1ec362a8ed4db835e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065118"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Ограничения безопасности для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server в Linux в настоящее время имеет следующие ограничения:

* Предоставляется политику паролей standard. Параметр MUST_CHANGE имеет единственный доступный параметр можно настроить таким образом.  
* Расширенное управление ключами не поддерживается. 
* Использование ключей, хранящихся в хранилище ключей Azure не поддерживается.
* SQL Server создает свой собственный самозаверяющий сертификат для шифрования подключений. SQL Server можно настроить для использования предоставленной сертификата для TLS пользователем. 

Дополнительные сведения о функциях безопасности, доступных в SQL Server, см. в разделе [центр обеспечения безопасности для ядра СУБД SQL Server и базы данных SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Следующие шаги

Общие задачи безопасности, см. в разделе [приступить к работе с помощью функций безопасности SQL Server на Linux](sql-server-linux-security-get-started.md). Для сценария, изменить TCP номер_порта, каталоги по SQL Server и настроить флагов трассировки или параметры сортировки, см. в разделе [Настройка SQL Server в Linux с помощью mssql-conf](sql-server-linux-configure-mssql-conf.md).
