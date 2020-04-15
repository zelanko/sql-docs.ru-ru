---
title: СЗЛГЕтТипИнфо (Парадокс Драйвер) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 693441c088865be85b18106a4c769a9f3f676f13
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295104"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (драйвер для Paradox)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах парадокса. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Имя типа (TYPE_NAME), возвращенное в таблицу, подготовленную **s'LGetTypeInfo,** будет названием, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будут возвращены в столбце SEARCHABLE для типов байт, Счетчик, Двойной, Одноместный, Длинный и Короткий. (Возможность LIKE может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, а затем выполнения сравнения.)
