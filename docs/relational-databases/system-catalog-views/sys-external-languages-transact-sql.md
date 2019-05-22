---
title: sys.external_languages (Transact-SQL) — SQL Server | Документация Майкрософт
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
ms.openlocfilehash: 1cef52f066a07032240d17f88297b02ba3f7e5fb
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995122"
---
# <a name="sysexternallanguages-transact-sql"></a>sys.external_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Это представление каталога содержит список внешних языков в базе данных. **R** и **Python** являются зарезервированными именами и внешних язык не могут быть созданы с именами соответствующих определенной.

## <a name="sysexternallanguages"></a>sys.external_languages

Sys.external_languages представления каталога перечислены по строке для каждого внешнего языка в базе данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_language_id |ssNoversion | Идентификатор внешнего языка|
|language |sysname |Имя внешнего языка. Уникален в пределах базы данных. R и Python — это зарезервированные имена каждого экземпляра|
|create_date |datetime2 |Дата и время создания|
|principal_id |ssNoversion |Идентификатор участника, которому принадлежит этот внешняя библиотека|

## <a name="see-also"></a>См. также  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [СОЗДАТЬ ВНЕШНИЙ ЯЗЫК](../../t-sql/statements/create-external-language-transact-sql.md) 
