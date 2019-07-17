---
title: sys.external_library_files (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a9666b58132feb79876c4e8074dc530440c05b2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68220347"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Перечислены строки для каждого файла, составляющего внешней библиотеки.

|Имя столбца |Тип данных |Описание|
|------|------|-----|
|external_library_id | ssNoversion |Идентификатор объекта внешней библиотеки. |
|content |varbinary(max) |Содержимое файла артефакта внешнюю библиотеку. |
|Платформы |tinyint |Идентификатор платформы узла, на котором установлен SQL Server. |
|platform_desc | nvarchar(60) |Имя платформы узла. Допустимые значения: «WINDOWS», «LINUX». |

### <a name="see-also"></a>См. также  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Управление пакетами для службы машинного обучения SQL Server](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
