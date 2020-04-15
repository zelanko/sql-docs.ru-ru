---
title: Управление текстовыми и имиджевыми столбцов (ru) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3ac58e59f66dd107a9523a42f5647c90b4fb737
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297724"
---
# <a name="managing-text-and-image-columns"></a>Управление столбцами text и image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**текст,** **ntext**, и данные **изображений** (также называются длинными данными) являются символ или типы данных бинарной строки, которые могут держать значения данных слишком велики, чтобы вписаться в **символ,** **varchar**, **двоичный**, или **varbinary** столбцы. Карты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типа **текстовых** данных для ODBC SQL_LONGVARCHAR типа данных; **ntext** карты для SQL_WLONGVARCHAR; и **карты изображений** для SQL_LONGVARBINARY. Некоторые объекты данных (например, длинные документы или большие битовые карты) слишком велики для их размещения в памяти. Для получения длинных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных из последовательных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] частей, драйвер Native Client ODBC позволяет приложению вызывать [S'LGetData.](../../relational-databases/native-client-odbc-api/sqlgetdata.md) Для отправки длинных данных в последовательных частях приложение может вызывать [S'LPutData.](../../relational-databases/native-client-odbc-api/sqlputdata.md) Параметры, для которых данные посылаются во время выполнения, называются параметрами c данными времени выполнения.  
  
 Приложение может на самом деле писать или извлекать любые типы данных (а не только длинные данные) с **помощью S'LPutData** или **S'LGetData,** хотя только **символ** и **двоичные** данные могут быть отправлены или извлечены по частям. Однако, если данные достаточно малы, чтобы поместиться в один буфер, как правило, нет никаких оснований для использования **S'LPutData** или **S'LGetData**. Гораздо проще привязать единичный буфер к параметру или столбцу.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязанные и непривязанные столбцы text и image](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Изменения с ведением журнала и без ведения журнала](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Данные времени выполнения и столбцы text, ntext или image](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
