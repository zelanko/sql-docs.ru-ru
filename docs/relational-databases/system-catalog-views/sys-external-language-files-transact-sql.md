---
title: sys. external_language_files (Transact-SQL) — SQL Server | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65995092"
---
# <a name="sysexternal_language_files-transact-sql"></a>sys. external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Это представление каталога содержит список файлов внешних расширений языка в базе данных. **R** и **Python** являются зарезервированными именами, и ни один внешний язык не может быть создан с этими конкретными именами.

При создании внешнего языка из file_spec в этом представлении отображаются само расширение и его свойства. В этом представлении будет содержаться одна запись для каждого языка, каждая ОС.

## <a name="sysexternal_languages"></a>sys.external_languages

Представление каталога sys. external_language_files содержит строку для каждого расширения внешнего языка в базе данных. Параметры

|Имя столбца |Тип данных | Description|
|------|------|------|
|external_language_id |INT | ИДЕНТИФИКАТОР внешнего языка|
|Содержимое|varbinary(max) |Содержимое файла внешнего расширения языка|
|file_name|nvarchar (266)|Имя файла расширения языка|
|платформа|tinyint;|Идентификатор платформы узла, на которой установлен SQL Server|
|platform_desc |nvarchar(60)|Имя платформы узла. Допустимые значения: "WINDOWS", "LINUX".|
|parameters|nvarchar(4000)|Внешний язык праметерс|
|environment_variables |nvarchar(4000)|Переменные среды внешнего языка|

## <a name="see-also"></a>См. также раздел  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНИЙ ЯЗЫК](../../t-sql/statements/create-external-language-transact-sql.md)  
