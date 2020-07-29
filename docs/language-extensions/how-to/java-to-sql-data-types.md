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
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 26c5e6f344d9fb0a14a21fa195214c4460673de0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748515"
---
# <a name="java-and-sql-server-supported-data-types"></a>Типы данных, поддерживаемые Java и SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этой статье сопоставляются типы данных и типы данных Java для структур данных и параметров в [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

В настоящее время поддерживаются следующие типы данных SQL и Java для наборов входных и выходных данных, а также для входных и выходных параметров.

| Тип данных SQL        | Тип данных Java | Комментарий | |
| ------------- |-------------|-|-|
| bit      | Логическое | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | String      | | |
| nvarchar(n) | String      | | |
| binary(n) | byte[]      | | |
| varbinary(n) | byte[]      | | |
| nvarchar(max) | String      | | |
| varbinary(max) | byte[]      | | |
| UNIQUEIDENTIFIER | String | | |
| char(n) | String | Поддерживаются только строки UTF8 | |
| varchar(n) | String | Поддерживаются только строки UTF8 | |
| varchar(max) | String | Поддерживаются только строки UTF8 | |
| Дата | java.sql.date  | | |
| NUMERIC | java.math.BigDecimal  | | |
| Decimal | java.math.BigDecimal  | | |
| money | java.math.BigDecimal  | | |
| smallmoney | java.math.BigDecimal  | | |
| smalldatetime | java.sql.timestamp  | | |
| DATETIME | java.sql.timestamp  | | |
| datetime2 | java.sql.timestamp  | | |


## <a name="next-steps"></a>Дальнейшие действия

+ [Как вызвать код Java в SQL Server](../how-to/call-java-from-sql.md)
