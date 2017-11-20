---
title: "Среда, соединения и атрибуты инструкции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dfe477bf0ca518d4f4e83d141a24bcb4c2640ed2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="environment-connection-and-statement-attributes"></a>Среда, соединения и атрибуты инструкции
ODBC определяет ряд атрибутов, связанных с сред, подключения или инструкции.  
  
 Атрибуты среды влияет на уровне всей среды, например ли пул соединений включен. Атрибуты среды устанавливаются с помощью **SQLSetEnvAttr** и полученный с **SQLGetEnvAttr**.  
  
 Атрибуты соединения влиять каждого подключения по отдельности, такими как время ожидания при попытке подключения к источнику данных, до истечения времени ожидания драйвером. Атрибуты соединения устанавливаются с помощью **SQLSetConnectAttr** и полученный с **SQLGetConnectAttr**. Дополнительные сведения об атрибутах соединения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Атрибуты инструкции влияют на каждой инструкции по отдельности, например, является ли инструкция должна выполняться асинхронно. Атрибуты инструкции устанавливаются с помощью **SQLSetStmtAttr** и полученный с **SQLGetStmtAttr**. Несколько атрибутов инструкции являются атрибуты, доступные только для чтения и не может быть задано. Например атрибут инструкции SQL_ATTR_ROW_NUMBER, который используется для извлечения номера текущей строки в курсор, доступно только для чтения. Дополнительные сведения об атрибутах инструкции см. в разделе [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Помимо атрибутами, определенными в ODBC драйвер можно определить собственные соединения и атрибуты инструкции. Атрибуты, определяемые драйвер должен быть зарегистрирован с помощью Open Group, чтобы убедиться, что двух поставщиков драйвер не назначается то же значение в целое число различия, собственные атрибуты. Дополнительные сведения см. в разделе [типов данных драйвера, дескрипторов типов, типов данных, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Полный список атрибутов см. в разделе [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), и [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Большинство атрибутов также описаны в описании функции ODBC, они влияют на.

