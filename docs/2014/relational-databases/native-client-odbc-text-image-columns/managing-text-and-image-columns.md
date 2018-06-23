---
title: Управление столбцами Text и Image | Документы Microsoft
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
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1316f093ac0d1f79c5155ae1be88df98f091bd8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193362"
---
# <a name="managing-text-and-image-columns"></a>Управление столбцами text и image
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **текст**, **ntext**, и **изображения** данных (также называемый длинных данных), символ или двоичных строковых типов данных, которые могут содержать значения данных слишком велик для **char**, **varchar**, **двоичных**, или **varbinary** столбцов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Текст** типа данных аналогичному типу данных ODBC SQL_LONGVARCHAR; **ntext** сопоставляется SQL_WLONGVARCHAR; а **изображения** сопоставляется SQL_LONGVARBINARY. Некоторые объекты данных (например, длинные документы или большие битовые карты) слишком велики для их размещения в памяти. Для получения данных большой длины из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] последовательными частями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента позволяет приложению вызывать [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Для отправления объемных данных частям, приложение может вызвать [SQLPutData](../native-client-odbc-api/sqlputdata.md). Параметры, для которых данные посылаются во время выполнения, называются параметрами c данными времени выполнения.  
  
 Приложение фактически можно создать или получить с любого типа данных (не только большой длины) **SQLPutData** или **SQLGetData**, хотя только **символ** и  **двоичный** могут передавать данные и отправлять по частям. Тем не менее, если данные помещаются в один буфер, обычно есть причин использовать **SQLPutData** или **SQLGetData**. Гораздо проще привязать единичный буфер к параметру или столбцу.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязанные и непривязанные столбцы text и image](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Изменения с ведением журнала и без ведения журнала](logged-vs-unlogged-modifications.md)  
  
-   [Данные времени выполнения и столбцы text, ntext или image](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  