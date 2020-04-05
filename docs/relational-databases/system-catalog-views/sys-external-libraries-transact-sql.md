---
title: sys.external_libraries (Трансакт-СЗЛ) Документы Майкрософт
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
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664436"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Поддерживает управление библиотеками пакетов, связанными с внешними временами выполнения, такими как R, Python и Java.

> [!NOTE]
> В SQL Server 2017 поддерживаются язык R и платформа Windows. R, Python и Java на платформах Windows и Linux поддерживаются в SQL Server 2019 и более поздних версий.

## <a name="sysexternal_libraries"></a>sys.external_libraries

Представление каталога sys.external_libraries перечисляет строку для каждой внешней библиотеки, загруженной в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |INT | Идентификатор внешнего объекта библиотеки. |
|name |sysname |Название внешней библиотеки. Уникален в базе данных на одного владельца.|
|principal_id |INT |Идентификатор директора, владеющего этой внешней библиотекой. |
|Язык | sysname | Название языка или время выполнения, поддерживающее внешнюю библиотеку. Допустимые значения: 'R', 'Python' и 'Java'. В будущем могут быть добавлены дополнительные время выполнения.|
|область |INT |0 для публичного охвата; 1 для частного объема |  
|scope_desc |Варчар (7) |Указывает, является ли пакет публичным или закрытым|

## <a name="see-also"></a>См. также  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [СОЗДАНИЕ ВНЕШНЕЙ БИБЛИОТЕКИ](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Установка новых пакетов R в SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [Установка новых пакетов Python в SQL Server](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  