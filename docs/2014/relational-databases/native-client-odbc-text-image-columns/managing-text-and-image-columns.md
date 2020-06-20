---
title: Управление столбцами Text и Image | Документация Майкрософт
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
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d7d5b0f48c68e8ac911f5e274c9afdb8cfe17d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049698"
---
# <a name="managing-text-and-image-columns"></a>Управление столбцами text и image
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]данные типа **Text**, **ntext**и **Image** (также называемые длинными данными) представляют собой символьные или двоичные строковые типы данных, которые могут содержать слишком большие значения данных для размещения в столбцах **char**, **varchar**, **binary**или **varbinary** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип данных **Text** сопоставляется с типом данных ODBC SQL_LONGVARCHAR. **ntext** сопоставляется с SQL_WLONGVARCHAR; **изображения** и сопоставляются с SQL_LONGVARBINARY. Некоторые объекты данных (например, длинные документы или большие битовые карты) слишком велики для их размещения в памяти. Для получения длинных данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] последовательных частей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента позволяет приложению вызывать [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Для отправки длинных данных в последовательных частях приложение может вызвать [SQLPutData](../native-client-odbc-api/sqlputdata.md). Параметры, для которых данные посылаются во время выполнения, называются параметрами c данными времени выполнения.  
  
 Приложение может на самом деле записывать или извлекать данные любого типа (не только длинные данные) с **SQLPutData** или **SQLGetData**, хотя в частях могут быть отправлены и получены только **символьные** и **двоичные** данные. Однако если данные достаточно малы для размещения в одном буфере, обычно нет причин использовать **SQLPutData** или **SQLGetData**. Гораздо проще привязать единичный буфер к параметру или столбцу.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Привязанные и непривязанные столбцы text и image](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Изменения с ведением журнала и без ведения журнала](logged-vs-unlogged-modifications.md)  
  
-   [Данные времени выполнения и столбцы text, ntext или image](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client (ODBC)](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
