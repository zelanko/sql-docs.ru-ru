---
title: Улучшения даты и времени | Документация Майкрософт
description: Улучшения даты и времени в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 170404a4f90be10c848c8f15b7663c330f67495a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989122"
---
# <a name="date-and-time-improvements"></a>Улучшения функций даты и времени
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В этом разделе описывается Драйвер OLE DB для SQL Server поддержки типов данных даты и времени, добавленных в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
 Дополнительные сведения об улучшениях даты и времени см. в разделе [улучшения &#40;даты и&#41;времени OLE DB](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md).  
  
 Сведения о примерах приложений, которые демонстрируют эту функцию, см. в разделе [Образцы программирования для SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Использование  
 В следующих разделах приводится описание различных способов использования новых типов даты и времени.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Использование Date как отдельного типа данных  
 Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], улучшенная поддержка типов даты и времени повышает эффективность использования типа OLE DB DBTYPE_DBDATE.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Использование Time как отдельного типа данных  
 OLE DB уже имеет тип данных, представляющий время с точностью до 1 секунды — DBTYPE_DBTIME.
  
 Новый тип данных времени [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеет точность до 100 наносекунд. Для этого требуется новый тип в драйвере OLE DB для SQL Server: DBTYPE_DBTIME2. Существующие приложения, не работающие с долями секунд, могут пользоваться столбцами time(0). Существующий тип OLE DB DBTYPE_TIME и соответствующие ему структуры должны работать правильно, если приложение не использует тип, возвращаемый в метаданных.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Использование Time как отдельного типа данных с расширенной точностью до долей секунд  
 Некоторым приложениям, например приложениям для управления производством и процессами, необходима возможность обработки времени с точностью до 100 наносекунд. Новый тип для этой цели в OLE DB — DBTYPE_DBTIME2.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Использование Datetime как отдельного типа данных с расширенной точностью до долей секунд  
 В OLE DB уже имеется определение типа с точностью до 1 наносекунды. Этот тип применяется в существующих приложениях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , однако ожидаемая точность таких приложений составляет лишь 1/300 секунды. Новый тип **datetime2(3)** несовместим напрямую с существующим типом datetime. Если есть риск, что он повлияет на работу приложения, необходимо при определении фактического типа на сервере пользоваться новым флагом DBCOLUMN.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Использование Datetime с расширенной точностью до долей секунд и часовым поясом  
 Некоторым приложениям необходимы значения даты-времени вместе со сведениями о часовом поясе. Это поддерживается новым типом DBTYPE_DBTIMESTAMPOFFSET.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Использование данных Date/Time/Datetime/Datetimeoffset с преобразованиями на стороне клиента, согласующимися с существующими преобразованиями  
 Преобразования расширены для согласования с преобразованиями всех типов данных даты и времени, представленных в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
