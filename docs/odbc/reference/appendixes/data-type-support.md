---
description: Поддержка типов данных
title: Поддержка типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ab0fd163713a7f6657d8ce446336f5c35a3dd00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456641"
---
# <a name="data-type-support"></a>Поддержка типов данных
Драйверы ODBC должны поддерживать хотя бы один SQL_CHAR и SQL_VARCHAR. Поддержка других типов данных определяется уровнем соответствия SQL-92 источника данных или драйвера. Приложение должно вызывать **SQLGetTypeInfo** для определения типов данных, поддерживаемых драйвером.  
  
 Дополнительные сведения о типах данных см. в разделе [Приложение D. типы данных](../../../odbc/reference/appendixes/appendix-d-data-types.md).
