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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a438823d1aa71eecb25c4935026c1b43e45842d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62637390"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Разработчикам приложений следует искать столбцы, определяемые драйвером, начиная с конца результирующего набора и далее в обратном порядке.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT или SQL_RESULT_COL|  
|ПОРЯДКОВЫЙ НОМЕР|Это столбец специфические для драйвера, который возвращается в конце результирующего набора. Тип SQL столбца представляет собой целое число.|
