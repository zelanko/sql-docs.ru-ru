---
title: Источник данных, имена и 64-разрядных операционных системах | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2248077b8efed3ebf11f871603a6513d6b9f4a02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612572"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Имена источников данных и 64-разрядные операционные системы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Для построения и запуска 32-разрядного приложения в 64-разрядной операционной системе необходимо создать источник данных ODBC с помощью программы администрирования ODBC (исполняемый файл %windir%\SysWOW64\odbcad32.exe).  
  
## <a name="remarks"></a>Примечания  
 В 64-разрядной операционной системе Windows есть два файла odbcad32.exe.  
  
-   %SystemRoot%\system32\odbcad32.exe используется для создания и поддержки имен источников данных для 64-разрядных приложений.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe используется для создания и поддержки имен источников данных для 32-разрядных приложений, в том числе и 32-разрядных приложений, работающих на 64-разрядной операционной системе.  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
