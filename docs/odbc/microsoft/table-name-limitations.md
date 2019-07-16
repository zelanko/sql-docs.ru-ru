---
title: Ограничения имен таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 152a0aa1e8d92424b2f60c49f44888de7d3e528c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939773"
---
# <a name="table-name-limitations"></a>Ограничения имен таблиц
Имена таблиц могут содержать любые допустимые символы (например, пробелы). Если имена таблиц, содержать любые символы, кроме буквы, цифры и символы подчеркивания, имя должно быть выделено, заключив его в обратной кавычки (').  
  
 Если используется драйвер Microsoft Excel, и ссылку на базу данных не уточняется именем таблицы, подразумевается базы данных по умолчанию. Если имя в Microsoft Excel содержит «!» символ, он будет автоматически преобразован для символа «$» вместо этого.  
  
 Имя таблицы Microsoft Excel, который ссылается на \<filename > поддерживается для Microsoft Excel 3.0 и 4.0 файлов. Имя таблицы Microsoft Excel, который ссылается на \<книги name > поддерживается для файлов Microsoft Excel 5.0, 7.0 или 97.  
  
 Если используется драйвер для dBASE, символы значение ASCII-больше 127 преобразуются в символы подчеркивания.  
  
 Когда используется драйвером Microsoft Access, имя таблицы ограничено 64 символами.  
  
 Когда используется драйвер для dBASE, Microsoft Excel 3.0 или 4.0, Paradox или текст, ключевые слова MS-DOS, CON, AUX, LPT1, LPT2 не должны использоваться как имена таблиц.
