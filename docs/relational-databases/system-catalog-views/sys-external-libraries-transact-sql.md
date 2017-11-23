---
title: "sys.external_libraries (Transact-SQL) | Документы Microsoft"
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
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: bb229022bcccfb9cdc8c419844d30335337575d4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Поддерживает управление пакет библиотеки, связанные с внешних сред выполнения, например R или Python.

## <a name="sysexternallibraries"></a>sys.external_libraries

Sys.external_libraries представление каталога содержит строку для каждой внешней библиотеки, который был загружен в базу данных.

|Имя столбца |Тип данных | Description|
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
