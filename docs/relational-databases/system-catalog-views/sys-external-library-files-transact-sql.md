---
title: sys.external_library_files (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: febfe235bd7f4711e8192ab7625491b72ac050ec
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001176"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Перечислены строки для каждого файла, составляющего внешней библиотеки.

|Имя столбца |Тип данных |Описание|
|------|------|-----|
|external_library_id | ssNoversion |Идентификатор объекта внешней библиотеки. |
|content |varbinary(max) |Содержимое файла артефакта внешнюю библиотеку. |
|Платформы |TINYINT |Идентификатор платформы узла, на котором установлен SQL Server. |
|platform_desc | nvarchar(60) |Имя платформы узла. Допустимые значения: «WINDOWS», «LINUX». |

### <a name="see-also"></a>См. также  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Управление пакетами для службы машинного обучения SQL Server](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
