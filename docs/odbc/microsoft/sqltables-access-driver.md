---
description: SQLTables (драйвер для Access)
title: SQLTables (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69dce4116064cdb7509f628fcc493e57c414666e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339920"
---
# <a name="sqltables-access-driver"></a>SQLTables (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Аргумент|Комментарии|  
|--------------|--------------|  
|*сзтаблеовнер*|Единственным допустимым аргументом для *сзтаблеовнер* является null, так как ни один из драйверов не поддерживает имена владельцев. Если для *сзтаблеовнер* ЗАДАНО значение null, возвращаются все таблицы. Значение NULL возвращается в столбец TABLE_OWNER.|  
|*сзтаблекуалифиер*|В столбце TABLE_QUALIFIER **SQLTables** вернет путь к файлу базы данных.|  
|*сзтаблетипе*|При использовании драйвера Microsoft Access "СИСТЕМная таблица" поддерживается для *сзтаблетипе* для системных таблиц, "синоним" поддерживается для присоединенных таблиц, а "View" поддерживается для запросов, возвращающих строки.|  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLTables](../../odbc/reference/syntax/sqltables-function.md)
