---
title: Данные времени выполнения и Text, ntext или столбцы изображений | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 90777c1f7f1ac50266eaf7fe473c5ca3b1c2f189
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189970"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Данные времени выполнения и столбцы text, ntext или image
  Данные времени выполнения ODBC позволяют приложениям работать с очень большими объемами данных в связанных столбцах или параметрах. При получении очень больших **текст**, **ntext**, или **изображения** столбцы, приложения не может иметь возможность просто выделить огромный буфер, привязать столбец в буфер и выборки Строка. При обновлении очень больших **текст**, **ntext**, или **изображения** столбцов, приложение может оказаться невозможным просто выделить огромный буфер, привязать его к маркеру параметра в SQL инструкции, а затем выполните инструкцию. В таких случаях приложение должно использовать [SQLGetData](../native-client-odbc-api/sqlgetdata.md) или [SQLPutData](../native-client-odbc-api/sqlputdata.md) с параметрами его данных во время выполнения.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](managing-text-and-image-columns.md)  
  
  