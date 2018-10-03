---
title: Данные времени выполнения и Text, ntext или столбцы изображений | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7c57cf6444e5833b6deee0dcae36d71b7a6430
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076751"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Данные времени выполнения и столбцы text, ntext или image
  Данные времени выполнения ODBC позволяют приложениям работать с очень большими объемами данных в связанных столбцах или параметрах. При получении очень больших **текст**, **ntext**, или **изображение** столбцы, приложение не может иметь возможность просто выделить огромный буфер, привязать столбец в буфер и получения Строка. При обновлении очень больших **текст**, **ntext**, или **изображение** столбцы, приложение не может иметь возможность просто выделить огромный буфер, привязать его к маркеру параметра в SQL инструкции, а затем выполняется инструкция. В этом случае приложение должно использовать [SQLGetData](../native-client-odbc-api/sqlgetdata.md) или [SQLPutData](../native-client-odbc-api/sqlputdata.md) с его параметрами данных во время выполнения.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](managing-text-and-image-columns.md)  
  
  
