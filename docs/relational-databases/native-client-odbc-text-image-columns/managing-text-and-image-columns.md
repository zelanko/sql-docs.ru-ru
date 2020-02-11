---
title: Управление столбцами Text и Image | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 221d83188a3d48fe5383a109b878c7b5a59bdad5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73758405"
---
# <a name="managing-text-and-image-columns"></a>Управление столбцами text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]данные типа **Text**, **ntext**и **Image** (также называемые длинными данными) представляют собой символьные или двоичные строковые типы данных, которые могут содержать слишком большие значения данных для размещения в столбцах **char**, **varchar**, **binary**или **varbinary** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Тип данных **Text** сопоставляется с типом данных ODBC SQL_LONGVARCHAR. **ntext** сопоставляется с SQL_WLONGVARCHAR; **изображения** и сопоставляются с SQL_LONGVARBINARY. Некоторые объекты данных (например, длинные документы или большие битовые карты) слишком велики для их размещения в памяти. Для получения длинных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из последовательных частей драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC для собственного клиента позволяет приложению вызывать [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Для отправки длинных данных в последовательных частях приложение может вызвать [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). Параметры, для которых данные посылаются во время выполнения, называются параметрами c данными времени выполнения.  
  
 Приложение может на самом деле записывать или извлекать данные любого типа (не только длинные данные) с **SQLPutData** или **SQLGetData**, хотя в частях могут быть отправлены и получены только **символьные** и **двоичные** данные. Однако если данные достаточно малы для размещения в одном буфере, обычно нет причин использовать **SQLPutData** или **SQLGetData**. Гораздо проще привязать единичный буфер к параметру или столбцу.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязанные и непривязанные столбцы типа Text и Image](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Изменения с ведением журнала и без ведения журнала](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Данные времени выполнения и столбцы text, ntext или image](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
