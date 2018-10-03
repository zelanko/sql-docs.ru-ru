---
title: IRowsetFastLoad (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35cee52e9a85989123bcb10d998d37ce86a28601
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215884"
---
# <a name="irowsetfastload-ole-db"></a>Метод IRowsetFastLoad (OLE DB)
  `IRowsetFastLoad` Интерфейс предоставляет поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операции массового копирования на основе памяти. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребители поставщика собственного клиента OLE DB используют интерфейс для быстрого добавления данных в существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE для сеанса, то будет невозможно считывать данные из наборов строк, возвращаемых впоследствии в этом сеансе. Если присвоить SSPROP_ENABLEFASTLOAD значение VARIANT_TRUE, то все наборы строк, созданные для сеанса, будут иметь тип IRowsetFastLoad. Наборы строк IRowsetFastLoad не поддерживают функциональные возможности получения данных из набора строк, поэтому чтение данных из наборов строк невозможно.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|Добавляет строку в набор строк для массового копирования.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Выполнение массового копирования данных с использованием интерфейса IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Отправка данных BLOB-объектов в SQL Server с помощью интерфейсов IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
