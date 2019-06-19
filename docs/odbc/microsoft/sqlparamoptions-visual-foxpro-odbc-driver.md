---
title: SQLParamOptions (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a66f0cd3a17baa9a09a5eeef2ade3d730f0a206b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62636664"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: уровне 1  
  
 Позволяет приложению указать несколько значений для набора параметров, назначенный [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). Возможность указать несколько значений для набора параметров полезно для массовой вставки и другие операции, необходимые для обработки той же инструкции SQL несколько раз с различными значениями параметров источника данных. Например, приложение может указать значения для набора параметров, связанных с **вставить** инструкции, а затем выполните **вставить** один раз для выполнения трех инструкции insert операции.  
  
 Дополнительные сведения см. в разделе [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) в *Справочник по программированию ODBC*.
