---
title: sys.external_language_files (Transact-SQL) — SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: dphansen
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
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0d1325311ef0b708f5a3abd5f4494e099863efc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65995092"
---
# <a name="sysexternallanguagefiles-transact-sql"></a>sys.external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Это представление каталога содержит список внешних языковые файлы расширения в базе данных. **R** и **Python** являются зарезервированными именами, поэтому создать внешние языки с такими именами невозможно.

При создании внешнего языка из file_spec само расширение и его свойства, перечислены в этом представлении. Это представление будет содержать одну запись для каждого языка, в ОС.

## <a name="sysexternallanguages"></a>sys.external_languages

Sys.external_language_files представления каталога перечислены по строке для каждого расширения внешним языком, который, в базе данных. Параметры

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_language_id |ssNoversion | Идентификатор внешнего языка|
|content|varbinary(max) |Содержимое файла расширения внешних языка|
|file_name|nvarchar(266)|Имя файла расширения языка|
|Платформы|tinyint|Идентификатор платформы узла, на котором установлен SQL Server|
|platform_desc |nvarchar(60)|Имя платформы узла. Допустимые значения: «WINDOWS», «LINUX».|
|Параметры|nvarchar(4000)|Внешние языковые prameters|
|environment_variables |nvarchar(4000)|Язык внешних переменных среды|

## <a name="see-also"></a>См. также  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНИЙ ЯЗЫК](../../t-sql/statements/create-external-language-transact-sql.md)  
