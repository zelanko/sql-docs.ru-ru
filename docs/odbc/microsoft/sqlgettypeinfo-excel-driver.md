---
title: СЗЛГЕтТипИнфо (Водитель Excel) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Excel Driver
- Excel driver [ODBC], SQLGetTypeInfo
ms.assetid: 708845be-e6a1-4677-8113-c52819a43fa4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64befe30be9ed7988e0c9348e9335eb632dd975c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295074"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (драйвер для Excel)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах Excel. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Имя типа (TYPE_NAME), возвращенное в таблицу, подготовленную **s'LGetTypeInfo,** будет названием, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будут возвращены в столбце SEARCHABLE для типов байт, Счетчик, Двойной, Одноместный, Длинный и Короткий. (Возможность LIKE может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, а затем выполнения сравнения.)  
  
 При использовании драйвера Microsoft Excel имена типа ODBC возвращаются в TYPE_NAME столбец, который возвращается **s'LGetTypeInfo.**
