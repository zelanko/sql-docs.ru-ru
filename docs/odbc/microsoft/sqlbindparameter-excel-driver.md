---
title: SQLBindParameter (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84f6e44f4849db81c591a791674878190f21e486
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298040"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (драйвер для Excel)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 При использовании драйвера Microsoft Excel для выполнения инструкции INSERT, в котором используется параметр, чтобы вставить значение NULL в столбец SQL_CHAR возвращает SQL_SUCCESS_WITH_INFO с кодом SQLSTATE 01004, «Данных усечена.»
