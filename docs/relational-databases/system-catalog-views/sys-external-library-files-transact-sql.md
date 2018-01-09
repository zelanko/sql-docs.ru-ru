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
ms.technology: 
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
ms.openlocfilehash: a03a50bdeda18d027fbad56e2cd4b86a261052b7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Содержит строку для каждого файла, составляющее внешней библиотеки.

|Имя столбца |Тип данных |Description|
|------|------|-----|
|external_library_id | ssNoversion |Идентификатор объекта, внешние библиотеки. |
|content |varbinary(max) |Содержимое файла артефакта внешней библиотеки. |
|Платформа |TINYINT |Идентификатор платформы узла, на котором установлен SQL Server. |
|platform_desc | nvarchar(60) |Имя платформы узла. Допустимые значения: «WINDOWS», «LINUX». |

### <a name="see-also"></a>См. также раздел  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[СОЗДАНИЕ ВНЕШНЕЙ БИБЛИОТЕКИ](../../t-sql/statements/create-external-library-transact-sql.md)  
[Пакет управления для службы SQL Server машины обучения](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
