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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070023"
---
# <a name="transferring-data-in-its-binary-form"></a>Передача данных в двоичной форме
Приложение может безопасно передавать данные (во внутренней форме, используемой указанной СУБД) между двумя источниками данных, использующими одну и ту же СУБД и аппаратную платформу. Для конкретного фрагмента данных типы данных SQL должны быть одинаковыми в исходном и целевом источниках данных. Тип данных C — SQL_C_BINARY.  
  
 Когда приложение вызывает **SQLFetch**, **SQLFetchScroll**или **SQLGetData** для получения данных из источника исходных данных, драйвер извлекает данные из источника данных и передает их без преобразования в место хранения типа SQL_C_BINARY. Когда приложение вызывает **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData или SQLSetPos** для отправки данных в целевой источник данных, драйвер получает данные из места хранения и передает их в целевой источник данных без преобразования.  
  
> [!NOTE]  
>  Приложения, которые передают данные (за исключением двоичных данных), не взаимодействуют между СУБД.  
  
 **Склкопидеск** можно использовать для копирования привязок строк из исходной СУБД в привязки параметров в целевой СУБД.
