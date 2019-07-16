---
title: IRowsetFastLoad (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c88a3d0a71305362acdf0ae28ef7eb4d75f5470f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051075"
---
# <a name="irowsetfastload-ole-db"></a>Метод IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Интерфейс **IRowsetFastLoad** обеспечивает поддержку операций массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в памяти. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребители поставщика собственного клиента OLE DB используют интерфейс для быстрого добавления данных в существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE для сеанса, то будет невозможно считывать данные из наборов строк, возвращаемых впоследствии в этом сеансе. Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE, то все наборы строк, созданные для сеанса, будут иметь тип IRowsetFastLoad. Наборы строк IRowsetFastLoad не поддерживают функциональные возможности получения данных из набора строк, поэтому чтение данных из наборов строк невозможно.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Добавляет строку в набор строк для массового копирования.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Выполнение массового копирования данных с использованием интерфейса IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Отправка данных BLOB-объектов в SQL Server с помощью интерфейсов IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
