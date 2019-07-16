---
title: Передача данных в двоичной форме | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2897f882dc9dcd78ee8b919de01126d6be510c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070023"
---
# <a name="transferring-data-in-its-binary-form"></a>Передача данных в двоичной форме
Приложение может безопасно передавать данные (Внутренняя формы, используемые указанную СУБД) между двумя источниками данных, которые используют же СУБД и аппаратной платформы. Для данного фрагмента данных типы данных SQL необходимо соответствующим образом в исходной и целевой источников данных. Тип данных C — SQL_C_BINARY.  
  
 Когда приложение вызывает **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** для получения данных из исходного источника данных, драйвер получает данные из данных источника и передает их, без преобразования в место хранения типа SQL_C_BINARY. Когда приложение вызывает **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData или SQLSetPos** для отправки данных целевой источник данных, драйвер получает данные из места хранения и передает их, без преобразования, для целевого источника данных.  
  
> [!NOTE]  
>  Приложения, передающие данные (за исключением двоичных данных) таким образом, не с возможностью взаимодействия между СУБД.  
  
 **SQLCopyDesc** можно использовать для копирования привязок строк из исходной СУБД для привязки параметров в целевой СУБД.
