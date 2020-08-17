---
description: SQLError (драйвер ODBC для Visual FoxPro)
title: SQLError (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09f901b72d292f962076bff2aa521c8214e8f0e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340260"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень ядра  
  
 Возвращает сведения об ошибке или состоянии последней ошибки. Драйвер поддерживает стек или список ошибок, которые могут быть возвращены для аргументов *хстмт*, *хдбк*и *хенв* в зависимости от того, как выполняется вызов **SqlError** . Очередь ошибок очищается после каждой инструкции.  
  
 В следующей таблице описаны аргументы **SqlError** и возвращаемые значения, используемые драйвером.  
  
|SQLError, аргумент|Описание возвращаемого значения|  
|-----------------------|------------------------------|  
|*сзсклстате*|Значение SQLSTATE, представленное ошибкой.|  
|*пфнативиррор*|Ненулевое значение указывает на [собственное сообщение об ошибке драйвера ODBC для Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Нулевое значение указывает, что ошибка была обнаружена драйвером и сопоставлена с соответствующим [кодом ошибки ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*сзеррормсг*|Текст для собственной ошибки или ошибки ODBC.|  
|*пкберрормсг*|Длина текста сообщения плюс длина идентификаторов.|  
  
 Дополнительные сведения о сообщениях об ошибках драйвера см. в разделе [Общие сведения об ошибках](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Дополнительные сведения об этой функции см. в разделе [SqlError](../../odbc/reference/syntax/sqlerror-function.md) в *справочнике программиста по ODBC*.
