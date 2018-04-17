---
title: sys.external_library_files (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
ms.openlocfilehash: 0278fa01c02bab9da03abb62c375c19e84d1d97d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Содержит строку для каждого файла, составляющее внешней библиотеки.

|Имя столбца |Тип данных |Описание|
|------|------|-----|
|external_library_id | int |Идентификатор объекта, внешние библиотеки. |
|content |varbinary(max) |Содержимое файла артефакта внешней библиотеки. |
|Платформа |tinyint |Идентификатор платформы узла, на котором установлен SQL Server. |
|platform_desc | nvarchar(60) |Имя платформы узла. Допустимые значения: «WINDOWS», «LINUX». |

### <a name="see-also"></a>См. также:  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[СОЗДАНИЕ ВНЕШНЕЙ БИБЛИОТЕКИ](../../t-sql/statements/create-external-library-transact-sql.md)  
[Пакет управления для службы SQL Server машины обучения](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
