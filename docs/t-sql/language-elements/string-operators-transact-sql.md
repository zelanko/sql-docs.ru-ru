---
description: Строковые операторы(Transact-SQL)
title: Строковые операторы (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], string concatenation
- plus sign (+)
- string concatenation operators
- + (string concatenation)
ms.assetid: ee4e715d-d8f1-4d0e-81b3-04573ec9f13c
author: rothja
ms.author: jroth
ms.openlocfilehash: fe780c6250f5e93292d3e54af66d5f01ebcf6bdf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445359"
---
# <a name="string-operators-transact-sql"></a>Строковые операторы(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает следующие операторы работы со строками. Операторы объединения строк могут объединять два и более следующих типов данных в одно выражение: 
* символьные или двоичные строки;
* столбцы 
* сочетание строк и имен столбцов. 

Операторы строк шаблонов могут соответствовать одному или нескольким символам в операции сравнения строк. LIKE и PATINDEX — примеры двух таких операций.  
  
## <a name="section-heading"></a>Заголовок раздела  
[+ (объединение строк)](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
  
[+= (присваивание объединения строк)](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
[% (подстановочный знак — один или несколько символов, которые должны совпасть)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)  
  
[[ ] (подстановочный знак — символы для сопоставления)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)  
  
[&#91;^&#93; (подстановочный знак — символы не для сопоставления)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)  
  
[_ (подстановочный знак — сравнение одного символа)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
