---
title: СЗЛГЕтТипИнфо (Драйвер текстовых файлов) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b70b58e4760959db102450b5f8b7beed042df95
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295004"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (драйвер для текстовых файлов)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах, специфийных для драйверов текста. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Имя типа (TYPE_NAME), возвращенное в таблицу, подготовленную **s'LGetTypeInfo,** будет названием, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будут возвращены в столбце SEARCHABLE для типов байт, Счетчик, Двойной, Одноместный, Длинный и Короткий. (Возможность LIKE может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, а затем выполнения сравнения.)  
  
 При использовании драйвера текста **S'LGetTypeInfo** возвращает CASE_SENSITIVE значение FALSE для типов текстовых данных (CHAR и LONGCHAR), когда типы данных фактически чувствительны к случаям.
