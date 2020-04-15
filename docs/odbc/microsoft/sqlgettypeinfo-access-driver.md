---
title: СЗЛГЕтТипИнфо (Драйвер доступа) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddfa9bd29f0834adf1c211f9b8a111db0b94d3fe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295154"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Имя типа (TYPE_NAME), возвращенное в таблицу, подготовленную **s'LGetTypeInfo,** будет названием, наиболее часто используемым источником данных.  
  
 SQL_ALL_EXCEPT_LIKE будут возвращены в столбце SEARCHABLE для типов байт, Счетчик, Двойной, Одноместный, Длинный и Короткий. (Возможность LIKE может быть достигнута путем преобразования значения в символ с помощью канонических функций преобразования ODBC, а затем выполнения сравнения.)
