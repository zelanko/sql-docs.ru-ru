---
title: Атрибуты среды, соединения и оператора Документы Майкрософт
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
ms.openlocfilehash: 86cecaf0b82c7b6d15b3f37262507d2cff0c3c10
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300934"
---
# <a name="environment-connection-and-statement-attributes"></a>Атрибуты среды, подключения и инструкций
ODBC определяет ряд атрибутов, связанных с средами, соединениями или операторами.  
  
 Атрибуты среды влияют на всю среду, например, включено ли объединение соединений. Атрибуты среды устанавливаются с **помощью S'LSetEnvAttr** и извлекаются с **помощью S'LGetEnvAttr.**  
  
 Атрибуты подключения влияют на каждое соединение индивидуально, например, как долго водитель должен ждать при попытке подключения к источнику данных до отсеивания. Атрибуты подключения устанавливаются с **помощью S'LSetConnectAttr** и извлекаются с **помощью S'LGetConnectAttr.** Для получения дополнительной информации [Connection Attributes](../../../odbc/reference/develop-app/connection-attributes.md)об атрибутах соединения см.  
  
 Атрибуты оператора влияют на каждую выписку индивидуально, например, следует ли выполнять заявление асинхронно. Атрибуты оператора устанавливаются с **помощью S'LSetStmtAttr** и извлекаются с **помощью S'LGetStmtAttr.** Некоторые атрибуты оператора являются атрибутами только для чтения и не могут быть установлены. Например, атрибут SQL_ATTR_ROW_NUMBER оператора, который используется для получения числа текущего строки в курсоре, только читается. Для получения дополнительной информации [Statement Attributes](../../../odbc/reference/develop-app/statement-attributes.md)об атрибутах оператора см.  
  
 В дополнение к атрибутам, определенным ODBC, драйвер может определить свои собственные атрибуты соединения и оператора. Атрибуты, определяемые драйверами, должны быть зарегистрированы в Open Group, чтобы гарантировать, что два поставщика драйверов не присваивают одинаковое значение целых значений различным, несвободным атрибутам. Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)  
  
 Полный список атрибутов можно ознакомьтесь с [си-ЛСЭтТенвАттр,](../../../odbc/reference/syntax/sqlsetenvattr-function.md) [СЗЛСетКоннЕКВаттр](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)и [СЗЛСетСтмттр.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) Большинство атрибутов также описаны в описании функции ODBC, на которую они влияют.
