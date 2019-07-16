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
ms.openlocfilehash: 1a33d449396b5cc80e8d29767708d2f9f16736fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987845"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Разработчикам приложений следует искать столбцы, определяемые драйвером, начиная с конца результирующего набора и далее в обратном порядке.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT или SQL_RESULT_COL|  
|ПОРЯДКОВЫЙ НОМЕР|Это столбец специфические для драйвера, который возвращается в конце результирующего набора. Тип SQL столбца представляет собой целое число.|
