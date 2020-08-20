---
description: SQLTables (драйвер ODBC для Visual FoxPro)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 089208ab612984283e3f87c4ad03aca0ccfa2b38
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471556"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень 1  
  
 Возвращает список имен таблиц, указанных параметром в инструкции **SQLTables** . Если параметр не указан, возвращает имена таблиц, хранящихся в текущем источнике данных. Драйвер возвращает сведения в виде результирующего набора.  
  
 Вызовы типа перечисления не получат запись результирующего набора для удаленных представлений или локальных параметризованных представлений. Однако вызов **SQLTables** с описателем уникального имени таблицы обнаружит совпадение для такого представления, если оно есть с таким именем; Это позволяет использовать API для проверки конфликтов имен перед созданием новой таблицы.  
  
> [!NOTE]  
>  Драйвер ODBC для Visual FoxPro различает [таблицы базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) и [свободные таблицы](../../odbc/microsoft/visual-foxpro-terminology.md), даже если оба типа таблиц хранятся в одном и том же каталоге в системе. Если источник данных является каталогом свободных таблиц, драйвер ODBC для Visual FoxPro не выполняет каталогизацию и не возвращает имена таблиц, связанных с базой данных.  
  
 Дополнительные сведения см. в разделе [SQLTables](../../odbc/reference/syntax/sqltables-function.md) в *справочнике программиста по ODBC*.
