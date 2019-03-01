---
title: sys.external_libraries (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a2f83d703566ae5a60fd027ff7f186205a0c404
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017540"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Поддерживает управление библиотеками пакетов, связанных с внешних сред выполнения, например R, Python и Java.

> [!NOTE]
> В SQL Server 2017 поддерживается языком R и платформы Windows. R, Python и Java на платформе Windows поддерживаются в SQL Server 2019 CTP 2.3. Поддержка Linux планируется в будущих выпусках.

## <a name="sysexternallibraries"></a>sys.external_libraries

Sys.external_libraries представление каталога содержит по строке для каждой внешней библиотеке, который был загружен в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |ssNoversion | Идентификатор объекта внешней библиотеки. |
|name |sysname |Имя внешней библиотеки. Уникален в пределах базы данных на одного владельца.|
|principal_id |ssNoversion |Идентификатор участника, которому принадлежит этот внешняя библиотека. |
|language | sysname | Имя используемого языка или среды выполнения, которая поддерживает внешнюю библиотеку. Допустимые значения: «R», «Python» и «Java». Дополнительные среды выполнения могут быть добавлены в будущем.|
|область |ssNoversion |0 для открытой области; 1 — закрытая область |  
|scope_desc |varchar(7) |Указывает, является ли пакет общедоступный или частный|

## <a name="see-also"></a>См. также  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Установка новых пакетов R в SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [Установка новых пакетов Python в SQL Server](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  