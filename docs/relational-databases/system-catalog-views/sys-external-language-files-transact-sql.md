---
title: sys. external_language_files (Transact-SQL) — SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a991761e26f8f63ae6431d7d242fb2625135d3ac
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627478"
---
# <a name="sysexternal_language_files-transact-sql"></a>sys. external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Это представление каталога содержит список файлов внешних расширений языка в базе данных. **R** и **Python** являются зарезервированными именами, поэтому создать внешние языки с такими именами невозможно.

При создании внешнего языка из file_spec в этом представлении отображаются само расширение и его свойства. В этом представлении будет содержаться одна запись для каждого языка, каждая ОС.

## <a name="sysexternal_languages"></a>sys.external_languages

Представление каталога sys. external_language_files содержит строку для каждого расширения внешнего языка в базе данных. Параметры

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_language_id |INT | ИДЕНТИФИКАТОР внешнего языка|
|содержимое|varbinary(max) |Содержимое файла внешнего расширения языка|
|file_name|nvarchar (266)|Имя файла расширения языка|
|platform|tinyint|Идентификатор платформы узла, на которой установлен SQL Server|
|platform_desc |nvarchar(60)|Имя платформы узла. Допустимые значения: "WINDOWS", "LINUX".|
|параметры|nvarchar(4000)|Внешний язык праметерс|
|environment_variables |nvarchar(4000)|Переменные среды внешнего языка|

## <a name="see-also"></a>Дополнительно  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНИЙ ЯЗЫК](../../t-sql/statements/create-external-language-transact-sql.md)  
