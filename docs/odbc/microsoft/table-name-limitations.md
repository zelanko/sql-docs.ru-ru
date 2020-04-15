---
title: Ограничение названия таблицы (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 738c563961eae56471f0238d9726a1ebb0bdc76e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289220"
---
# <a name="table-name-limitations"></a>Ограничения имен таблиц
Имена таблиц могут содержать любые допустимые символы (например, пробелы). Если названия таблиц содержат какие-либо символы, кроме букв, цифр и подчеркнутостей, имя должно быть разграничено, прилагая его к задним кавычкам (').  
  
 При использовании драйвера Microsoft Excel и некончня названия таблицы подчняется ссылка на базу данных, подразумевается база данных по умолчанию. Если имя в Microsoft Excel включает символ "!" вместо этого будет автоматически переведено на символ "$".  
  
 Название таблицы Microsoft Excel, в которое ссылается на имя файла \<> поддерживается для файлов Microsoft Excel 3.0 и 4.0. Название таблицы Microsoft Excel, в которое ссылается> на имя рабочей книги, \<поддерживается для файлов Microsoft Excel 5.0, 7.0 или 97 файлов.  
  
 При использовании драйвера dBASE символы со значением ASCII больше 127 преобразуются в подчеркивание.  
  
 При использовании драйвера Microsoft Access имя таблицы ограничено 64 символами.  
  
 При использовании dBASE, Microsoft Excel 3.0 или 4.0, Paradox или Text драйвера в качестве названий таблиц не следует использовать специальные ключевые слова MS-DOS CON, AUX, LPT1 и LPT2.
