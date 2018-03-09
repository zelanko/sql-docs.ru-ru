---
title: "Дата и время улучшениях | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9b1d0d9d-1f6e-4399-8f61-e23f9a486a7a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4708cdab10f80f6a41aa006621484d5a9848885
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="date-and-time-improvements"></a>Дата и время усовершенствования
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  В этом разделе описана поддержка в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] новых типов данных даты и времени, которые были введены в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
 Дополнительные сведения об улучшениях даты и времени см. в разделе [даты и времени усовершенствования &#40; OLE DB &#41;](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md) и [даты и времени усовершенствования &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
 Сведения о примерах приложений, которые демонстрируют эту функцию, см. в разделе [Образцы программирования для SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Использование  
 В следующих разделах приводится описание различных способов использования новых типов даты и времени.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Использование Date как отдельного типа данных  
 Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], расширенная поддержка типов даты-времени делает использование типа SQL_TYPE_DATE ODBC (SQL_DATE для приложений ODBC 2.0) и типа DBTYPE_DBDATE OLE DB более эффективным.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Использование Time как отдельного типа данных  
 OLE DB уже имеет тип данных, представляющий время с точностью до 1 секунды — DBTYPE_DBTIME. В ODBC его эквивалентом является тип SQL_TYPE_TIME (SQL_TIME для приложений ODBC 2.0).  
  
 Новый [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеет тип данных времени секунд с точностью до 100 наносекунд. Это требует новые типы в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client: DBTYPE_DBTIME2 (OLE DB) и SQL_SS_TIME2 (ODBC). Существующие приложения, не работающие с долями секунд, могут пользоваться столбцами time(0). Существующие типы OLE DB DBTYPE_TIME и ODBC SQL_TYPE_TIME и соответствующие им структуры должны работать правильно, если приложение не использует тип, возвращаемый в метаданных.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Использование Time как отдельного типа данных с расширенной точностью до долей секунд  
 Некоторым приложениям, например приложениям для управления производством и процессами, необходима возможность обработки времени с точностью до 100 наносекунд. Эту возможность обеспечивают новые типы DBTYPE_DBTIME2 (OLE DB) и SQL_SS_TIME2 (ODBC).  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Использование Datetime как отдельного типа данных с расширенной точностью до долей секунд  
 В OLE DB уже имеется определение типа с точностью до 1 наносекунды. Этот тип применяется в существующих приложениях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], однако ожидаемая точность таких приложений составляет лишь 1/300 секунды. Новый тип **datetime2(3)** несовместим напрямую с существующим типом datetime. Если есть риск, что он повлияет на работу приложения, необходимо при определении фактического типа на сервере пользоваться новым флагом DBCOLUMN.  
  
 ODBC также определяет тип с точностью до 1 наносекунды. Этот тип применяется в существующих приложениях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], однако ожидаемая точность таких приложений составляет всего 3 миллисекунды. Новый тип **datetime2(3)** несовместим напрямую с существующим типом данных **datetime** . Тип**datetime2(3)** имеет точность до одной миллисекунды, а **datetime** — 1/300 секунды. В ODBC приложение имеет возможность выяснить тип данных сервера по полю дескриптора SQL_DESC_TYPE_NAME. Поэтому существующий тип SQL_TYPE_TIMESTAMP (SQL_TIMESTAMP для приложений ODBC 2.0) может использоваться для обоих типов.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Использование Datetime с расширенной точностью до долей секунд и часовым поясом  
 Некоторым приложениям необходимы значения даты-времени вместе со сведениями о часовом поясе. Эта возможность поддерживается новыми типами DBTYPE_DBTIMESTAMPOFFSET (OLE DB) и SQL_SS_TIMESTAMPOFFSET (ODBC).  
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Использование данных Date/Time/Datetime/Datetimeoffset с преобразованиями на стороне клиента, согласующимися с существующими преобразованиями  
 Стандарт ODBC описывает преобразования между существующими типами даты, времени и отметок времени. Они расширены для согласования с преобразованиями всех типов данных даты-времени, представленных в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
