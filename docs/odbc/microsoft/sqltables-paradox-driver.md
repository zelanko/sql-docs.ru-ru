---
title: SQLTables (Драйвер Paradox) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLTables
- SQLTables function [ODBC], Paradox Driver
ms.assetid: d68adad6-97bd-4b47-bcf9-0102aafb00d4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 48cbc19506a7f695433489c952f53864b614a05e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949026"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (драйвер для Paradox)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Paradox. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*сзтаблеовнер*|Единственным допустимым аргументом для *сзтаблеовнер* является null, так как ни один из драйверов не поддерживает имена владельцев. Если для *сзтаблеовнер* ЗАДАНО значение null, возвращаются все таблицы. Значение NULL возвращается в столбец TABLE_OWNER.|  
|*сзтаблекуалифиер*|В столбце TABLE_QUALIFIER **SQLTables** вернет путь к каталогу.|  
|*сзтаблетипе*|Для файлов Paradox "TABLE" — это единственный поддерживаемый тип таблицы.|  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLTables](../../odbc/reference/syntax/sqltables-function.md)
