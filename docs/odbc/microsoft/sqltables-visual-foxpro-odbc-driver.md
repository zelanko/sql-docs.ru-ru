---
title: SQLTables (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e134b2870c4506e725f2900b83d1118e42b55d15
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63219123"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Возвращает список имен таблиц, указанного в параметре в **SQLTables** инструкции. Если параметр не указан, возвращает имена таблиц, хранимых в текущем источнике данных. Драйвер возвращает данные в виде результирующего набора.  
  
 Перечисления типа вызывает метод не получит запись результирующего набора для представления удаленного или локального параметризованных представлений. Тем не менее вызов **SQLTables** с уникальной таблицы спецификатор имени будет найти совпадения для такого представления, при его наличии с таким же именем; благодаря этому API, который будет использоваться для проверки конфликтов имени до создания новой таблицы.  
  
> [!NOTE]  
>  Драйвер Visual FoxPro ODBC различает [таблицы базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) и [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md), даже в том случае, если оба типа таблиц хранятся в том же каталоге, в вашей системе. Если источник данных является каталогом свободного таблиц, драйвер ODBC для Visual FoxPro каталога или не возвращает имена всех таблиц, которые связаны с базой данных.  
  
 Дополнительные сведения см. в разделе [SQLTables](../../odbc/reference/syntax/sqltables-function.md) в *Справочник по программированию ODBC*.
