---
title: Метод iRowsetFastLoad (OLE DB) | Документы Microsoft
description: Метод IRowsetFastLoad (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 747f3169052becb9b4ed5c31d3faddd0de08d8e3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="irowsetfastload-ole-db"></a>Метод IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IRowsetFastLoad** интерфейс обеспечивает поддержку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] памяти операциях массового копирования. Драйвер OLE DB для SQL Server используют этот интерфейс для быстрого добавления данных в существующий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы.  
  
 Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE для сеанса, то будет невозможно считывать данные из наборов строк, возвращаемых впоследствии в этом сеансе. Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE, будет иметь тип IRowsetFastLoad все наборы строк, созданные для сеанса. Наборы строк iRowsetFastLoad не поддерживают функциональные возможности; Таким образом не удается прочитать данные из этих наборов строк.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Добавляет строку в набор строк для массового копирования.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)   
 [Массовое копирование данных с использованием интерфейса IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Отправка данных BLOB на SQL SERVER с помощью IROWSETFASTLOAD и ISEQUENTIALSTREAM & #40; OLE DB & #41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
