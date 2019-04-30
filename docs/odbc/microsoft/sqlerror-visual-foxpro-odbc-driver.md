---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3014c5c2af1a0ef8e5f485c790089e4807834446
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313280"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: Уровня ядра  
  
 Возвращает сведения об ошибках и состоянии о последней ошибке. Драйвер поддерживает стека или список ошибок, которые могут быть возвращены для *hstmt*, *hdbc*, и *henv* аргументами, в зависимости от того, как вызов **SQLError**  выполняется. В очередь ошибок очищается после каждой инструкции.  
  
 В следующей таблице описаны **SQLError** аргументы и возвращаемые значения, используемые драйвером.  
  
|Аргумент SQLError|Описание возвращаемого значения|  
|-----------------------|------------------------------|  
|*szSQLState*|Значение SQLSTATE, представленный ошибку.|  
|*pfNativeError*|Ненулевое значение указывает на [Visual FoxPro ODBC драйвер собственного сообщение об ошибке](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Нулевое значение указывает обнаружен драйвером и сопоставлены в соответствующую ошибку [кодов ошибок ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Текст для собственная ошибка или ошибка ODBC.|  
|*pcbErrorMsg*|Длина текста сообщения, а также длину идентификаторов.|  
  
 Дополнительные сведения о сообщениях об ошибках драйвера см. в разделе [Обзор сообщений ошибка](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Дополнительные сведения об этой функции см. в разделе [SQLError](../../odbc/reference/syntax/sqlerror-function.md) в *Справочник по программированию ODBC*.
