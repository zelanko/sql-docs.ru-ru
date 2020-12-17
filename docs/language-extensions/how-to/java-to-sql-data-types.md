---
title: Типы данных Java
titleSuffix: SQL Server Language Extensions
description: Сопоставление типов данных из Java с SQL Server для входных и выходных структур данных, а также для входных параметров sp_execute_external_script.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: d5703470849f627cca87c471ea666b7c1b0e7e85
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471745"
---
# <a name="java-and-sql-server-supported-data-types"></a>Типы данных, поддерживаемые Java и SQL Server
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

В этой статье сопоставляются типы данных и типы данных Java для структур данных и параметров в [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

В настоящее время поддерживаются следующие типы данных SQL и Java для наборов входных и выходных данных, а также для входных и выходных параметров.

| Тип данных SQL        | Тип данных Java | Комментарий |
| ------------- |-------------|-|
| bit      | Логическое | |
| Tinyint      | short      | |
| Smallint | short      | |
| Int | INT      | |
| Real | FLOAT      | |
| Bigint | long      | |
| FLOAT | double      | |
| nchar(n) | String      | |
| nvarchar(n) | String      | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | String      | |
| varbinary(max) | byte[]      | |
| UNIQUEIDENTIFIER | String | |
| char(n) | String | Поддерживаются только строки UTF8 |
| varchar(n) | String | Поддерживаются только строки UTF8 |
| varchar(max) | String | Поддерживаются только строки UTF8 |
| Дата | java.sql.date  | |
| NUMERIC | java.math.BigDecimal  | |
| Decimal | java.math.BigDecimal  | |
| money | java.math.BigDecimal  | |
| smallmoney | java.math.BigDecimal  | |
| smalldatetime | java.sql.timestamp  | |
| DATETIME | java.sql.timestamp  | |
| datetime2 | java.sql.timestamp  | |


## <a name="next-steps"></a>Дальнейшие действия

+ [Как вызвать код Java в SQL Server](../how-to/call-java-from-sql.md)