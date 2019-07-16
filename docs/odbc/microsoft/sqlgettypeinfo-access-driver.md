---
title: SQLGetTypeInfo (драйвер для Access) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 788f0b8c69636ad9bf93de73632abc911a0fb0e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898756"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Имя типа (TYPE_NAME), возвращаемых в таблицу, созданные **SQLGetTypeInfo** будет использоваться имя, чаще всего используется в источнике данных.  
  
 SQL_ALL_EXCEPT_LIKE будет возвращаться в столбце с возможностью поиска байт, счетчик, Double, Single, долго и Short типов данных. (LIKE возможность достигается путем преобразования значения в символ, с помощью преобразования канонические функции ODBC, выполнению сравнения.)
