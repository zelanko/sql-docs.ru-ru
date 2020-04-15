---
title: СЗЛТаблицы (Парадокс Драйвер) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aa13b5395d8f3c2cb470a4eff1b1ef02a43bad53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299293"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (драйвер для Paradox)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах парадокса. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*szTableВладелец*|Единственным веским аргументом для *szTableOwner* является NULL, потому что ни один из драйверов не поддерживает имена владельцев. С *набором szTableOwner* null все таблицы возвращаются. NULL возвращается в TABLE_OWNER колонке.|  
|*szTableQualifier*|В TABLE_QUALIFIER колонке **S'LTables** вернет путь в каталог.|  
|*SzTableType*|Для файлов Paradox "TABLE" является единственным поддерживаемым типом таблицы.|  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLTables](../../odbc/reference/syntax/sqltables-function.md)
