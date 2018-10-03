---
title: Среды, подключения и атрибуты инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e77be71458eb10e97a82c925d34141a7bcaf1dc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685938"
---
# <a name="environment-connection-and-statement-attributes"></a>Атрибуты среды, подключения и инструкций
ODBC определяет ряд атрибутов, которые связаны с среды, подключения или инструкции.  
  
 Атрибуты среды влияет на всю среду, например является ли пул подключений включен. Атрибуты среды задаются с помощью **SQLSetEnvAttr** и получить с помощью **SQLGetEnvAttr**.  
  
 Атрибуты соединения влиять каждого подключения по отдельности, такими как время ожидания при попытке подключения к источнику данных, до истечения времени ожидания драйвером. Атрибуты соединения устанавливаются с помощью **SQLSetConnectAttr** и получить с помощью **SQLGetConnectAttr**. Дополнительные сведения об атрибутах соединения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Атрибуты инструкции влияют на каждый оператор по отдельности, например ли инструкция должна выполняться асинхронно. Атрибуты инструкции устанавливаются с помощью **SQLSetStmtAttr** и получить с помощью **SQLGetStmtAttr**. Несколько атрибутов инструкции атрибуты только для чтения и не может быть задано. Например атрибут инструкции SQL_ATTR_ROW_NUMBER, который используется для получения числа текущей строки в курсоре, доступен только для чтения. Дополнительные сведения о атрибуты инструкции, см. в разделе [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 В дополнение к атрибутам, определенном ODBC драйвер можно определить собственные подключения и атрибуты инструкции. Атрибуты, определяемые драйвером должны быть зарегистрированы с помощью Open Group, чтобы убедиться, что двух поставщиков драйвер не назначайте значение целого числа различных, собственные атрибуты. Дополнительные сведения см. в разделе [типов данных драйвера, типы дескрипторов, типы сведений, диагностические типы и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Полный список атрибутов, см. в разделе [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), и [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Большинство атрибутов также описаны в описании функции ODBC, они влияют на.
