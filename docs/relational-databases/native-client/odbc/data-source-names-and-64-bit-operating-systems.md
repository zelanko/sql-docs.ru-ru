---
title: Источник данных, имена и 64-разрядных операционных системах | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a9ce739eaaf8ee5c2a95a7e883f002a300ef1a63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>Имена источников данных и 64-разрядные операционные системы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Для построения и запуска 32-разрядного приложения в 64-разрядной операционной системе необходимо создать источник данных ODBC с помощью программы администрирования ODBC (исполняемый файл %windir%\SysWOW64\odbcad32.exe).  
  
## <a name="remarks"></a>Замечания  
 В 64-разрядной операционной системе Windows есть два файла odbcad32.exe.  
  
-   %SystemRoot%\system32\odbcad32.exe используется для создания и поддержки имен источников данных для 64-разрядных приложений.  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe используется для создания и поддержки имен источников данных для 32-разрядных приложений, в том числе и 32-разрядных приложений, работающих на 64-разрядной операционной системе.  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server & #40; ODBC & #41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
