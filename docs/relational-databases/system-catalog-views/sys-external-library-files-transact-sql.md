---
title: "sys.external_library_files (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.external_library_files catalog view
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: a3196218bbb886544a77c2fd1184c806591b16e6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Содержит строку для каждого файла, составляющее внешней библиотеки.

|Имя столбца |Тип данных |Description|
|------|------|-----|
|external_library_id | int |Идентификатор объекта, внешние библиотеки. |
|content |varbinary(max) |Содержимое файла артефакта внешней библиотеки. |
|Платформа |tinyint |Идентификатор платформы узла, на котором установлен SQL Server. |
|platform_desc | nvarchar(60) |Имя платформы узла. Допустимые значения: «WINDOWS», «LINUX». |

### <a name="see-also"></a>См. также:  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[СОЗДАНИЕ ВНЕШНЕЙ БИБЛИОТЕКИ](../../t-sql/statements/create-external-library-transact-sql.md)  
[Пакет управления для службы SQL Server машины обучения](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
