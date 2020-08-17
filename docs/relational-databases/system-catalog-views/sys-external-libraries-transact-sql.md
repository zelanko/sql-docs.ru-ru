---
description: sys.external_libraries (Transact-SQL)
title: sys. external_libraries (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/25/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
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
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 6dcc1b8f7cddc785203dc2430c2f1a4dce4b4d39
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88377580"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE [SQL Server 2017 SQL MI](../../includes/applies-to-version/sqlserver2017-asdbmi.md)]

Поддерживает управление библиотеками пакетов, связанными с внешними средами выполнения, такими как R, Python и Java.

> [!NOTE]
> В SQL Server 2017 поддерживаются язык R и платформа Windows. R, Python и Java на платформах Windows и Linux поддерживаются в SQL Server 2019 и более поздних версий. В Azure SQL Управляемый экземпляр поддерживаются R и Python.

## <a name="sysexternal_libraries"></a>sys.external_libraries

Представление каталога sys. external_libraries содержит строку для каждой внешней библиотеки, которая была передана в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |INT | Идентификатор объекта внешней библиотеки. |
|name |sysname |Имя внешней библиотеки. Уникален в пределах базы данных на владельца.|
|principal_id |INT |Идентификатор участника, владеющего этой внешней библиотекой. |
|язык | sysname | Имя языка или среды выполнения, поддерживающей внешнюю библиотеку. Допустимые значения: "R", "Python" и "Java". В будущем могут быть добавлены дополнительные среды выполнения.|
|scope |INT |0 для общедоступной области; 1 для закрытой области |  
|scope_desc |varchar (7) |Указывает, является ли пакет открытым или закрытым|

## <a name="see-also"></a>См. также раздел  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНЮЮ БИБЛИОТЕКУ](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Установка новых пакетов R](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [Установка новых пакетов Python](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  
