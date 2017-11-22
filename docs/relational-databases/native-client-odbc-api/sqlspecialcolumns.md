---
title: "SQLSpecialColumns | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ff6889d81489b0009d4c48b5194d772abaec014
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  При запросе идентификаторов строк (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** возвращает пустой результирующий набор (без строк данных) для любой запрошенной области, отличной от SQL_SCOPE_CURROW. Сформированный результирующий набор определяет, что столбцы допустимы только внутри этой области.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает псевдостолбцы для идентификаторов. **SQLSpecialColumns** результирующий набор будет идентифицировать все столбцы как SQL_PC_NOT_PSEUDO.  
  
 **SQLSpecialColumns** может быть выполнена для статического курсора. Попытка выполнить **SQLSpecialColumns** на обновляемых (управляемые набором ключей или динамического) возвращает значение SQL_SUCCESS_WITH_INFO, указывающее, что тип курсора был изменен.  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLSpecialColumns улучшенных функций работы с данными в формате даты-времени  
 Сведения о значениях, возвращаемых для столбцов DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH и DECIMAL_DIGTS для типов даты и времени, см. в разделе [метаданные каталога](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные общие сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>Поддержка функцией SQLSpecialColumns определяемых пользователем типов больших данных CLR  
 **SQLSpecialColumns** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLSpecialColumns](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
