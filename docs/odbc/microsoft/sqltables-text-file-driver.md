---
title: SQLTables (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7fcdf9cc41a55d1e529001ae7183ef9fa833363b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67949014"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверам текстовых файлов. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*сзтаблеовнер*|Единственным допустимым аргументом для *сзтаблеовнер* является null, так как ни один из драйверов не поддерживает имена владельцев. Если для *сзтаблеовнер* ЗАДАНО значение null, возвращаются все таблицы. Значение NULL возвращается в столбец TABLE_OWNER.|  
|*сзтаблекуалифиер*|В столбце TABLE_QUALIFIER **SQLTables** вернет путь к каталогу.|  
|*сзтаблетипе*|"TABLE" — это единственный поддерживаемый тип таблицы.<br /><br /> При использовании текстового драйвера список файлов, возвращаемых функцией **SQLTables** , определяется расширениями файлов в **списке расширения** в диалоговом окне « **Установка текста ODBC** ».|
