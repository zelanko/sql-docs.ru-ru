---
title: СЗЛГетТипИнфо (драйвер dBASE) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 711652e22318d089b02fe8e79cb592f0a42dfff9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295134"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (драйвер для dBASE)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах dBASE. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Имя типа (TYPE_NAME), возвращенное в таблицу, подготовленную **s'LGetTypeInfo,** будет названием, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будут возвращены в столбце SEARCHABLE для типов байт, Счетчик, Двойной, Одноместный, Длинный и Короткий. (Возможность LIKE может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, а затем выполнения сравнения.)
