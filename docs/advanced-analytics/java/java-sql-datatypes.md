---
title: Типы данных Java, поддерживаемые в SQL Server 2019 - службы машинного обучения SQL Server
description: Сопоставление типов данных, из Java к SQL Server для структур входные и выходные данные, а также для входных параметров в sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4c0f691b8bb389c2da2001d19f0684b7f928f707
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017820"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java и SQL Server поддерживаемые типы данных

В этой статье сопоставляет типы данных SQL Server и типами данных Java для структур данных и параметров на [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Типы данных для наборов данных

Для входных и выходных наборов данных в настоящее время поддерживаются следующие типы данных SQL и Java.

| Тип данных SQL        | Тип данных Java | Комментарий | |
| ------------- |-------------|-|
| bit      | boolean | |
| Tinyint      | short      | |
| Smallint | short      | |
| int | ssNoversion      | |
| Real | FLOAT      | |
| Bigint | long      | |
| FLOAT | double      | |
| nchar(n) | String      | |
| nvarchar(n) | String  | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | String | |
| varbinary(max) | byte[] | |
| UNIQUEIDENTIFIER | String | |
| char(n) | String | Поддерживается только на UTF8 строки |
| varchar(n) | String | Поддерживается только на UTF8 строки |
| varchar(max) | String | Поддерживается только на UTF8 строки |

## <a name="data-types-for-input-parameters"></a>Типы данных для входных параметров

Для входных параметров в настоящее время поддерживаются следующие типы данных SQL и Java.

| Тип данных SQL        | Тип данных Java | Комментарий | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | ssNoversion      | | |
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
| char(n) | String | Поддерживается только на UTF8 строки | |
| varchar(n) | String | Поддерживается только на UTF8 строки | |
| varchar(max) | String | Поддерживается только на UTF8 строки | |

## <a name="see-also"></a>См. также

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Расширение языка Java в SQL Server](extension-java.md)