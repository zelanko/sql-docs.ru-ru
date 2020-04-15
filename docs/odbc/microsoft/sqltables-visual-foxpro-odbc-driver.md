---
title: S'LTables (Визуальный водитель FoxPro ODBC) Документы Майкрософт
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
ms.openlocfilehash: 5467fc8c1717d5ceb548b3950a0894fd2a1b4499
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299291"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие API ODBC: Уровень 1  
  
 Возвращает список имен таблиц, указанных параметром, в заявлении **S'LTables.** Если параметр не указан, возвращаетимена таблицы, хранящиеся в текущем источнике данных. Водитель возвращает информацию в результате набора.  
  
 Вызовы типа Enumeration не будут получать запись набора результатов для удаленных представлений или локальных параметризированных представлений. Тем не менее, вызов в **S'LTables** с уникальным игоподобным названием таблицы найдет совпадение для такого представления, если он присутствует с этим именем; это позволяет использовать API для проверки конфликтов имен до создания новой таблицы.  
  
> [!NOTE]  
>  Драйвер Visual FoxPro ODBC различает [таблицы баз данных](../../odbc/microsoft/visual-foxpro-terminology.md) и [свободные таблицы,](../../odbc/microsoft/visual-foxpro-terminology.md)даже если оба типа таблиц хранятся в одном каталоге системы. Если ваш источник данных является каталогом свободных таблиц, Visual FoxPro ODBC Driver не каталогизирует и не возвращает имена любых таблиц, связанных с базой данных.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference*см. [SQLTables](../../odbc/reference/syntax/sqltables-function.md)
