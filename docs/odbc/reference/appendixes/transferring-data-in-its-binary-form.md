---
title: "Передача данных в двоичной форме | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7241124d7297dd661c3aef08701af0cc15d77d1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="transferring-data-in-its-binary-form"></a>Передача данных в двоичной форме
Приложения для безопасного обмена данными (в форме внутренней, используемые в указанную СУБД) между двух источников данных, использующих одинаковые СУБД и аппаратной платформы. Для данного фрагмента данных типы данных SQL должен совпадать в исходной и целевой источников данных. Тип данных C — SQL_C_BINARY.  
  
 Когда приложение вызывает **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** для получения данных из исходного источника данных, драйвер получает данные из данных исходные и передает ее, без преобразования в расположение хранилища типа SQL_C_BINARY. Когда приложение вызывает **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData или SQLSetPos** передавать данные в целевой источник данных, драйвер получает данные из места хранения и передает его, без преобразования в целевой источник данных.  
  
> [!NOTE]  
>  Приложения, передачи данных (за исключением двоичных данных) таким образом, не поддерживает возможность взаимодействия между СУБД.  
  
 **SQLCopyDesc** можно использовать для копирования привязок строк из исходной СУБД привязки параметров в целевой СУБД.
