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
ms.openlocfilehash: 1adbde1b3df38d2b602f1ec42a2c96f36e8bd67b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996375"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень 1  
  
 Позволяет приложению указать несколько значений для набора параметров, назначенных [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). Возможность указывать несколько значений для набора параметров полезна при выполнении операций с массовыми вставками и другой работой, требующей, чтобы источник данных несколько раз обрабатывал одну и ту же инструкцию SQL с различными значениями параметров. Например, приложение может указать три набора значений для набора параметров, связанных с инструкцией **INSERT** , а затем выполнить инструкцию **INSERT** один раз для выполнения трех операций вставки.  
  
 Дополнительные сведения см. в разделе [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) в *справочнике программиста по ODBC*.
