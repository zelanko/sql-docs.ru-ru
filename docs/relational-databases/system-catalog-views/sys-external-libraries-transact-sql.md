---
title: sys. external_libraries (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
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
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6b1bfc00b403fa76f692db78593ed4c0e6b53ce8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664436"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Поддерживает управление библиотеками пакетов, связанными с внешними средами выполнения, такими как R, Python и Java.

> [!NOTE]
> В SQL Server 2017 поддерживаются язык R и платформа Windows. R, Python и Java на платформах Windows и Linux поддерживаются в SQL Server 2019 и более поздних версий.

## <a name="sysexternal_libraries"></a>sys.external_libraries

Представление каталога sys. external_libraries содержит строку для каждой внешней библиотеки, которая была передана в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |INT | Идентификатор объекта внешней библиотеки. |
|name |sysname |Имя внешней библиотеки. Уникален в пределах базы данных на владельца.|
|principal_id |INT |Идентификатор участника, владеющего этой внешней библиотекой. |
|Язык | sysname | Имя языка или среды выполнения, поддерживающей внешнюю библиотеку. Допустимые значения: "R", "Python" и "Java". В будущем могут быть добавлены дополнительные среды выполнения.|
|scope |INT |0 для общедоступной области; 1 для закрытой области |  
|scope_desc |varchar (7) |Указывает, является ли пакет открытым или закрытым|

## <a name="see-also"></a>См. также  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНЮЮ БИБЛИОТЕКУ](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Установка новых пакетов R в SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [Установка новых пакетов Python в SQL Server](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  