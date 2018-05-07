---
title: SQLError (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26a639c0342072d9c188bb82c92acfb9a7da3fb5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Возвращает ошибки или состояния сведения о последней ошибке. Драйвер поддерживает стека или список ошибок, которые могут быть возвращены для *hstmt*, *hdbc*, и *henv* аргументы, в зависимости от того, как вызов **SQLError**  выполняется. Ошибка очереди очищается после каждой инструкции.  
  
 В следующей таблице описаны **SQLError** аргументы и возвращаемые значения, используемые драйвером.  
  
|Аргумент SQLError|Описание возвращаемое значение|  
|-----------------------|------------------------------|  
|*szSQLState*|Значение SQLSTATE, представленный ошибку.|  
|*pfNativeError*|Ненулевое значение указывает [Visual FoxPro ODBC драйвера собственного сообщение об ошибке](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Нулевое значение указывает ошибка обнаружена драйвером и сопоставлен соответствующий [кодов ошибок ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Текст для собственной ошибки или ошибка ODBC.|  
|*pcbErrorMsg*|Длина текста сообщения плюс длина идентификаторов.|  
  
 Дополнительные сведения о сообщениях об ошибках драйверов см. в разделе [Обзор сообщения ошибки](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Дополнительные сведения об этой функции см. в разделе [SQLError](../../odbc/reference/syntax/sqlerror-function.md) в *справочнике программиста ODBC*.
