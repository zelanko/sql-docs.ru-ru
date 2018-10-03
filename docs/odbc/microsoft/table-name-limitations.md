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
manager: craigg
ms.openlocfilehash: 31c1703bc03a2881e7b9b96989b8949cc81aba7b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707052"
---
# <a name="table-name-limitations"></a>Ограничения имен таблиц
Имена таблиц могут содержать любые допустимые символы (например, пробелы). Если имена таблиц, содержать любые символы, кроме буквы, цифры и символы подчеркивания, имя должно быть выделено, заключив его в обратной кавычки (').  
  
 Если используется драйвер Microsoft Excel, и ссылку на базу данных не уточняется именем таблицы, подразумевается базы данных по умолчанию. Если имя в Microsoft Excel содержит «!» символ, он будет автоматически преобразован для символа «$» вместо этого.  
  
 Имя таблицы Microsoft Excel, который ссылается на \<filename > поддерживается для Microsoft Excel 3.0 и 4.0 файлов. Имя таблицы Microsoft Excel, который ссылается на \<книги name > поддерживается для файлов Microsoft Excel 5.0, 7.0 или 97.  
  
 Если используется драйвер для dBASE, символы значение ASCII-больше 127 преобразуются в символы подчеркивания.  
  
 Когда используется драйвером Microsoft Access, имя таблицы ограничено 64 символами.  
  
 Когда используется драйвер для dBASE, Microsoft Excel 3.0 или 4.0, Paradox или текст, ключевые слова MS-DOS, CON, AUX, LPT1, LPT2 не должны использоваться как имена таблиц.
