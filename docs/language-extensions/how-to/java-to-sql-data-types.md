---
title: Типы данных Java, поддерживаемые в SQL Server 2019
titleSuffix: SQL Server Language Extensions
description: Сопоставление типов данных из Java с SQL Server для входных и выходных структур данных, а также для входных параметров sp_execute_external_script.
author: dphansen
ms.author: davidph
ms.date: 09/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9daca9c607befe077fcccec20385a36c82b04c6f
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "73588838"
---
# <a name="java-and-sql-server-supported-data-types"></a>Типы данных, поддерживаемые Java и SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этой статье сопоставляются типы данных и типы данных Java для структур данных и параметров в [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

В настоящее время поддерживаются следующие типы данных SQL и Java для наборов входных и выходных данных, а также для входных и выходных параметров.

| Тип данных SQL        | Тип данных Java | Комментарий | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | INT      | | |
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
| SMALLMONEY | java.math.BigDecimal  | | |
| smalldatetime | java.sql.timestamp  | | |
| DATETIME | java.sql.timestamp  | | |
| datetime2 | java.sql.timestamp  | | |


## <a name="next-steps"></a>Следующие шаги

+ [Как вызвать код Java в SQL Server](../how-to/call-java-from-sql.md)
