---
description: sys.external_languages (Transact-SQL) — SQL Server
title: sys.external_languages (Transact-SQL) — SQL Server | Документация Майкрософт
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
ms.openlocfilehash: 107a775af7379167716993e4d95b524e361eed31
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97477485"
---
# <a name="sysexternal_languages-transact-sql"></a>sys.external_languages (Transact-SQL)
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Это представление каталога содержит список внешних языков в базе данных. **R** и **Python** являются зарезервированными именами, поэтому создать внешние языки с такими именами невозможно.

## <a name="sysexternal_languages"></a>sys.external_languages

Представление каталога sys.external_languages отображает строку для каждого внешнего языка в базе данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_language_id |INT | ИДЕНТИФИКАТОР внешнего языка|
|язык |sysname |Имя внешнего языка. Уникален в пределах базы данных. R и Python являются зарезервированными именами для каждого экземпляра|
|create_date |datetime2 |Дата и время создания|
|principal_id |INT |Идентификатор участника, владеющего этой внешней библиотекой|

## <a name="see-also"></a>См. также раздел  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНИЙ ЯЗЫК](../../t-sql/statements/create-external-language-transact-sql.md) 
