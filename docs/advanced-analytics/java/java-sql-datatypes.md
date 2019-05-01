---
title: Типы данных Java, поддерживаемые в SQL Server 2019 - расширения языка SQL Server
description: Сопоставление типов данных, из Java к SQL Server для структур входные и выходные данные, а также для входных параметров в sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 14a2bc5594b16610dfb8278ab82a9e7b8b22fea6
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473600"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java и SQL Server поддерживаемые типы данных

В этой статье сопоставляет типы данных SQL Server и типами данных Java для структур данных и параметров на [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Типы данных для наборов данных

Для входных и выходных наборов данных в настоящее время поддерживаются следующие типы данных SQL и Java.


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

## <a name="next-steps"></a>Следующие шаги

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Расширение языка Java в SQL Server](extension-java.md)
