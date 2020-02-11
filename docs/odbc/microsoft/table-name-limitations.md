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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67939773"
---
# <a name="table-name-limitations"></a>Ограничения имен таблиц
Имена таблиц могут содержать любые допустимые символы (например, пробелы). Если имена таблиц содержат любые символы, кроме букв, цифр и знаков подчеркивания, имя должно быть заключено в кавычки (').  
  
 Если используется драйвер Microsoft Excel и имя таблицы не уточняется ссылкой на базу данных, подразумевается база данных по умолчанию. Если имя в Microsoft Excel содержит символ "!", он будет автоматически преобразован в символ "$".  
  
 Имя таблицы Microsoft Excel, ссылающееся \<на filename>, поддерживается для файлов Microsoft Excel 3,0 и 4,0. Имя таблицы Microsoft Excel, ссылающееся \<на имя книги>, поддерживается для файлов Microsoft Excel 5,0, 7,0 или 97.  
  
 При использовании драйвера dBASE символы со значением ASCII, превышающим 127, преобразуются в знаки подчеркивания.  
  
 При использовании драйвера Microsoft Access длина имени таблицы ограничена 64 символами.  
  
 Если используется драйвер dBASE, Microsoft Excel 3,0 или 4,0, Paradox или Text, в качестве имен таблиц не следует использовать специальные ключевые слова MS-DOS CON, AUX, LPT1 и LPT2.
