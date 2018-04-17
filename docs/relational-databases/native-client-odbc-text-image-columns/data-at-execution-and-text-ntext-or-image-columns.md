---
title: Данные времени выполнения и Text, ntext или столбцы изображений | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
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
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a7b2e9fb51696b6a9f0c31b25719338b24097e47
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Данные времени выполнения и столбцы text, ntext или image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Данные времени выполнения ODBC позволяют приложениям работать с очень большими объемами данных в связанных столбцах или параметрах. При получении очень больших **текст**, **ntext**, или **изображения** столбцы, приложения не может иметь возможность просто выделить огромный буфер, привязать столбец в буфер и выборки Строка. При обновлении очень больших **текст**, **ntext**, или **изображения** столбцов, приложение может оказаться невозможным просто выделить огромный буфер, привязать его к маркеру параметра в SQL инструкции, а затем выполните инструкцию. В таких случаях приложение должно использовать [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) или [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md) с параметрами его данных во время выполнения.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
