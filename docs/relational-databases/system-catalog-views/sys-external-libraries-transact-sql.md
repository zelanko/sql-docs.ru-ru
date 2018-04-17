---
title: sys.external_libraries (Transact-SQL) | Документы Microsoft
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
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d8fa8a4d41cff452379c420b712f13b2d4415a74
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Поддерживает управление пакет библиотеки, связанные с внешних сред выполнения, например R или Python.

## <a name="sysexternallibraries"></a>sys.external_libraries

Sys.external_libraries представление каталога содержит строку для каждой внешней библиотеки, который был загружен в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |int | Идентификатор объекта, внешние библиотеки. |
|имя |sysname |Имя внешней библиотеки. Уникален в пределах одного владельца базы данных.|
|principal_id |int |Идентификатор участника, которому принадлежит этот внешней библиотеки. |
|language | sysname | Имя языка или среды выполнения, которая поддерживает внешней библиотеки. Допустимые значения: «R». Дополнительные среды выполнения могут быть добавлены в будущем.|
|область |int |0 для открытой области; 1 для закрытая область |  
|scope_desc |varchar(7) |Указывает, является ли пакет открытым или закрытым|


## <a name="see-also"></a>См. также:  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[СОЗДАНИЕ ВНЕШНЕЙ БИБЛИОТЕКИ](../../t-sql/statements/create-external-library-transact-sql.md)  
[Пакет управления для SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
