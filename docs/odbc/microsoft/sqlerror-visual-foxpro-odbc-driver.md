---
title: S'LОшибка (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
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
ms.openlocfilehash: 0d1247217905187cfb2dbaca6d7b7b562d0175bd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298684"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: базовый уровень  
  
 Возвращает информацию об ошибке или статусе последней ошибки. Драйвер поддерживает стек или список ошибок, которые могут быть возвращены для *hstmt,* *hdbc*, и *henv* аргументы, в зависимости от того, как вызов **на S'LError** производится. Очередь ошибки смывается после каждой выписки.  
  
 В следующей таблице описаны аргументы **s'LError** и значения возврата, используемые драйвером.  
  
|Аргумент «Ошибка в сопере»|Описание значения возврата|  
|-----------------------|------------------------------|  
|*szS'LState*|Значение для S'LSTATE, представленное ошибкой.|  
|*pfNativeОшибка*|Ненулевое значение указывает на [визуальное сообщение о выводе о выводе о выводе о выводе об ошибке драйвера FoxPro ODBC.](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md) Значение нуля указывает на то, что ошибка была обнаружена драйвером и отображана в соответствующем [Коде ошибки ODBC.](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)|  
|*szErrorMsg*|Текст для ошибки родной или ошибки ODBC.|  
|*pcbErrorMsg*|Длина текста сообщения плюс длина идентификаторов.|  
  
 Для получения дополнительной информации [Error Messages Overview](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md)о сообщениях об ошибках драйвера см. Для получения более подробной информации об *ODBC Programmer's Reference*этой функции, [см.](../../odbc/reference/syntax/sqlerror-function.md)
