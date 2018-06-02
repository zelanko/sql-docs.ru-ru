---
title: Управление столбцами Text и Image | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 300caa16e74ee36e740c901a295c1c30c1723d33
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707242"
---
# <a name="managing-text-and-image-columns"></a>Управление столбцами text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **текст**, **ntext**, и **изображения** данных (также называемый длинных данных), символ или двоичных строковых типов данных, которые могут содержать значения данных слишком велик для **char**, **varchar**, **двоичных**, или **varbinary** столбцов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Текст** типа данных аналогичному типу данных ODBC SQL_LONGVARCHAR; **ntext** сопоставляется SQL_WLONGVARCHAR; а **изображения** сопоставляется SQL_LONGVARBINARY. Некоторые объекты данных (например, длинные документы или большие битовые карты) слишком велики для их размещения в памяти. Для получения данных большой длины из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] последовательными частями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента позволяет приложению вызывать [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Для отправления объемных данных частям, приложение может вызвать [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). Параметры, для которых данные посылаются во время выполнения, называются параметрами c данными времени выполнения.  
  
 Приложение фактически можно создать или получить с любого типа данных (не только большой длины) **SQLPutData** или **SQLGetData**, хотя только **символ** и  **двоичный** могут передавать данные и отправлять по частям. Тем не менее, если данные помещаются в один буфер, обычно есть причин использовать **SQLPutData** или **SQLGetData**. Гораздо проще привязать единичный буфер к параметру или столбцу.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязанные и непривязанные столбцы text и image](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Изменения с ведением журнала и без ведения журнала](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Данные времени выполнения и столбцы text, ntext или image](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
