---
description: Атрибуты среды, подключения и инструкций
title: Атрибуты среды, соединения и оператора | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6bc37e05f2c8847ff9a4828a5d2e9e7456732a41
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482957"
---
# <a name="environment-connection-and-statement-attributes"></a>Атрибуты среды, подключения и инструкций
ODBC определяет ряд атрибутов, связанных с средами, соединениями или инструкциями.  
  
 Атрибуты среды влияют на всю среду, например, включена ли поддержка пулов соединений. Атрибуты среды задаются с помощью **SQLSetEnvAttr** и извлекаются с помощью **SQLGetEnvAttr**.  
  
 Атрибуты подключения влияют на каждое подключение по отдельности, например время ожидания драйвера при попытке подключения к источнику данных до истечения времени ожидания. Атрибуты соединения задаются с помощью **SQLSetConnectAttr** и извлекаются с помощью **SQLGetConnectAttr**. Дополнительные сведения об атрибутах соединения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Атрибуты инструкции влияют на каждую инструкцию по отдельности, например, должна ли инструкция выполняться асинхронно. Атрибуты инструкции задаются с помощью **SQLSetStmtAttr** и извлекаются с помощью **SQLGetStmtAttr**. Некоторые атрибуты инструкции являются атрибутами только для чтения и не могут быть заданы. Например, атрибут оператора SQL_ATTR_ROW_NUMBER, который используется для получения номера текущей строки курсора, доступен только для чтения. Дополнительные сведения об атрибутах операторов см. в разделе [атрибуты инструкций](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Помимо атрибутов, определенных ODBC, драйвер может определять собственные атрибуты соединения и инструкции. Атрибуты, определенные драйвером, должны быть зарегистрированы в Open Group, чтобы два поставщика драйверов не присвоить одно и то же целое значение разным атрибутам. Дополнительные сведения см. в разделе [зависящие от драйвера типы данных, Типы дескрипторов, типы сведений, типы диагностики и атрибуты](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Полный список атрибутов см. в разделе [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)и [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md). Большинство атрибутов также описаны в описании функции ODBC, на которые они влияют.
