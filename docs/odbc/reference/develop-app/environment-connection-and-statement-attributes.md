---
title: Среда, соединения и атрибуты инструкции | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b8e3ee068d160269336de15ce1ddef3e7c78d58
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="environment-connection-and-statement-attributes"></a>Среда, соединения и атрибуты инструкции
ODBC определяет ряд атрибутов, связанных с сред, подключения или инструкции.  
  
 Атрибуты среды влияет на уровне всей среды, например ли пул соединений включен. Атрибуты среды устанавливаются с помощью **SQLSetEnvAttr** и полученный с **SQLGetEnvAttr**.  
  
 Атрибуты соединения влиять каждого подключения по отдельности, такими как время ожидания при попытке подключения к источнику данных, до истечения времени ожидания драйвером. Атрибуты соединения устанавливаются с помощью **SQLSetConnectAttr** и полученный с **SQLGetConnectAttr**. Дополнительные сведения об атрибутах соединения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Атрибуты инструкции влияют на каждой инструкции по отдельности, например, является ли инструкция должна выполняться асинхронно. Атрибуты инструкции устанавливаются с помощью **SQLSetStmtAttr** и полученный с **SQLGetStmtAttr**. Несколько атрибутов инструкции являются атрибуты, доступные только для чтения и не может быть задано. Например атрибут инструкции SQL_ATTR_ROW_NUMBER, который используется для извлечения номера текущей строки в курсор, доступно только для чтения. Дополнительные сведения об атрибутах инструкции см. в разделе [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Помимо атрибутами, определенными в ODBC драйвер можно определить собственные соединения и атрибуты инструкции. Атрибуты, определяемые драйвер должен быть зарегистрирован с помощью Open Group, чтобы убедиться, что двух поставщиков драйвер не назначается то же значение в целое число различия, собственные атрибуты. Дополнительные сведения см. в разделе [типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Полный список атрибутов см. в разделе [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), и [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Большинство атрибутов также описаны в описании функции ODBC, они влияют на.
