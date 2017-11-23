---
title: "Имя ограничения таблицы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4a9c803701e377bd345ea35b8ba528692eee98f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="table-name-limitations"></a>Имя ограничения таблицы
Имена таблиц могут содержать любые допустимые символы (например, пробелы). Если имена таблиц содержит любые символы, кроме буквы, цифры и знаки подчеркивания, имя должны быть разделены заключать в обратной кавычки (').  
  
 При использовании драйвера Microsoft Excel, ссылку на базу данных не уточняется именем таблицы, подразумевается базы данных по умолчанию. Если имя в Microsoft Excel включает в себя «!» символ, он автоматически преобразуется в символ «$» вместо.  
  
 Имя таблицы Microsoft Excel, который ссылается на \<имя файла > поддерживается для Microsoft Excel 3.0 и 4.0 файлы. Имя таблицы Microsoft Excel, который ссылается на \<имя книги > поддерживается для файлов Microsoft Excel 5.0, 7.0 или 97.  
  
 При использовании драйвера dBASE символов больше 127 значение ASCII преобразуются в символы подчеркивания.  
  
 Когда используется драйвер Microsoft Access, имя таблицы — длиннее 64 символов.  
  
 При использовании dBASE драйвера Microsoft Excel 3.0 или 4.0, Paradox или текст, ключевые слова MS-DOS, CON, AUX, LPT1, LPT2 не должны использоваться как имена таблиц.
