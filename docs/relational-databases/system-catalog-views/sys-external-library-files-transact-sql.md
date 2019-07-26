---
title: sys. external_library_files (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
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
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d7af0a7fcb639ae3beab6216e77f9b7b95a398da
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471094"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys. external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Содержит строку для каждого файла, составляющего внешнюю библиотеку.

|Имя столбца |Тип данных |Описание|
|------|------|-----|
|external_library_id | ssNoversion |Идентификатор объекта внешней библиотеки. |
|content |varbinary(max) |Содержимое артефакта внешнего файла библиотеки. |
|платформы |tinyint |Идентификатор платформы узла, на которой установлен SQL Server. |
|platform_desc | nvarchar(60) |Имя платформы узла. Допустимые значения: "WINDOWS", "LINUX". |

### <a name="see-also"></a>См. также  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[СОЗДАТЬ ВНЕШНЮЮ БИБЛИОТЕКУ](../../t-sql/statements/create-external-library-transact-sql.md)  
[Управление пакетами для службы SQL Server Машинное обучение](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
