---
description: sys.external_language_files (Transact-SQL) — SQL Server
title: sys.external_language_files (Transact-SQL) — SQL Server | Документация Майкрософт
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
monikerRange: '>=sql-server-ver15'
ms.openlocfilehash: f09590931848f963ebe62736d4a890c0cf11ed0d
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477465"
---
# <a name="sysexternal_language_files-transact-sql"></a>sys.external_language_files (Transact-SQL)
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Это представление каталога содержит список файлов внешних расширений языка в базе данных. **R** и **Python** являются зарезервированными именами, поэтому создать внешние языки с такими именами невозможно.

При создании внешнего языка из file_spec в этом представлении отображаются само расширение и его свойства. В этом представлении будет содержаться одна запись для каждого языка, каждая ОС.

## <a name="sysexternal_languages"></a>sys.external_languages

В представлении каталога sys.external_language_files перечислены строки для каждого расширения внешнего языка в базе данных. Параметры

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_language_id |INT | ИДЕНТИФИКАТОР внешнего языка|
|содержимое|varbinary(max) |Содержимое файла внешнего расширения языка|
|file_name|nvarchar (266)|Имя файла расширения языка|
|platform|tinyint|Идентификатор платформы узла, на которой установлен SQL Server|
|platform_desc |nvarchar(60)|Имя платформы узла. Допустимые значения: "WINDOWS", "LINUX".|
|параметры|nvarchar(4000)|Внешний язык праметерс|
|environment_variables |nvarchar(4000)|Переменные среды внешнего языка|

## <a name="see-also"></a>См. также раздел  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНИЙ ЯЗЫК](../../t-sql/statements/create-external-language-transact-sql.md)  
