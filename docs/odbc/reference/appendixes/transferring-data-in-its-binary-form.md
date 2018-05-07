---
title: Передача данных в двоичной форме | Документы Microsoft
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
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc85c74325a442cb3ba23db24f38aa21fb7be07d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="transferring-data-in-its-binary-form"></a>Передача данных в двоичной форме
Приложения для безопасного обмена данными (в форме внутренней, используемые в указанную СУБД) между двух источников данных, использующих одинаковые СУБД и аппаратной платформы. Для данного фрагмента данных типы данных SQL должен совпадать в исходной и целевой источников данных. Тип данных C — SQL_C_BINARY.  
  
 Когда приложение вызывает **SQLFetch**, **SQLFetchScroll**, или **SQLGetData** для получения данных из исходного источника данных, драйвер получает данные из данных исходные и передает ее, без преобразования в расположение хранилища типа SQL_C_BINARY. Когда приложение вызывает **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData или SQLSetPos** передавать данные в целевой источник данных, драйвер получает данные из места хранения и передает его, без преобразования в целевой источник данных.  
  
> [!NOTE]  
>  Приложения, передачи данных (за исключением двоичных данных) таким образом, не поддерживает возможность взаимодействия между СУБД.  
  
 **SQLCopyDesc** можно использовать для копирования привязок строк из исходной СУБД привязки параметров в целевой СУБД.
