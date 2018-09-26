---
title: Типы данных Java, поддерживаемые в SQL Server 2019 | Документация Майкрософт
description: Сопоставление типов данных, из Java к SQL Server для структур входные и выходные данные, а также для входных параметров в sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3510b53510514daa125382fc10ea33285fe44a80
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715438"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java и SQL Server поддерживаемые типы данных

В этой статье сопоставляет типы данных SQL Server и типами данных Java для структур данных и параметров на [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Типы данных для наборов данных

Для входных и выходных наборов данных в настоящее время поддерживаются следующие типы данных SQL и Java.

| Тип SQL        | Тип Java | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Строка (Юникод)      | | |
| nvarchar(n) | Строка (Юникод)      | | |
| binary(n) | byte[]      | | |
| varbinary(n) | byte[]      | | |

## <a name="data-types-for-input-parameters"></a>Типы данных для входных параметров

Для входных параметров в настоящее время поддерживаются следующие типы данных SQL и Java.

| Тип SQL        | Тип Java | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| int | ssNoversion      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Строка (Юникод)      | | |
| nvarchar(n) | Строка (Юникод)      | | |
| binary(n) | byte[]      | | |
| varbinary(n) | byte[]      | | |
| nvarchar(max) | Строка (Юникод)      | | |
| varbinary(max) | byte[]      | | |

## <a name="see-also"></a>См. также

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Расширение языка Java в SQL Server](extension-java.md)