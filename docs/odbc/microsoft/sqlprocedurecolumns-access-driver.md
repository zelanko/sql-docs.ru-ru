---
title: SQLProcedureColumns (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be17776ac6b6879140a7c57bede1b3cb539d97be
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299464"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Разработчики приложений должны найти столбцы, определяемые драйвером, начиная с конца результирующего набора и продолжая переходить назад.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT или SQL_RESULT_COL|  
|ПОРЯДКОВЫЙ номер|Это столбец, зависящий от драйвера, который возвращается в конце результирующего набора. Тип SQL столбца является целым числом.|
