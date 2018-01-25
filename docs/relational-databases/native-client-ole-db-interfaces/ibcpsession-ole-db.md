---
title: "Интерфейс IBCPSession (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: COM
helpviewer_keywords: IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
caps.latest.revision: "28"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 650a7e2a10e6ebb45d8662e1cb33a3a42f7dfe1e
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="ibcpsession-ole-db"></a>Интерфейс IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IBCPSession** интерфейс обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] операций массового копирования. **IBCPSession** интерфейс, предоставленный в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком OLE DB для собственного клиента под тем же уровнем как сеансы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты источника данных являются фабриками объектов сеанса поставщика OLE DB для собственного клиента и операций массового копирования указываются в свойстве соединения SSPROP_ENABLEBULKCOPY. Кроме того, свойство SSPROP_ENABLEFASTLOAD должно быть установлено в значение TRUE.  
  
 Вызов метода **IDBCreateSession::CreateSession** приведет к созданию объекта **BulkCopySession** . Все методы массового копирования, основанные на файлах, доступные через объект **IBCPSession** , можно вызывать с помощью этих объектов **IBCPSession** интерфейса **IBCPSession** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента поддерживает операции на основе памяти массового копирования через [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) интерфейса.  
  
 Дополнительные сведения об использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента для операций массового копирования в разделе [выполнение операций массового копирования](../../relational-databases/native-client/features/performing-bulk-copy-operations.md).  
  
 Пример, демонстрирующий использование **IBCPSession** интерфейса см. в разделе [IBCPSession::BCPDone &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|Создает привязку между переменными программы и столбцами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPColumns &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Метод IBCPSession::BCPControl &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|Устанавливает параметры для операции массового копирования.|  
|[IBCPSession::BCPDone &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|Фиксирует оставшиеся строки для отправки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPExec &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|Выполняет операцию массового копирования.|  
|[IBCPSession::BCPInit &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|Инициализирует структуру массового копирования, выполняет проверку ошибок, проверяет правильность имен файла данных и файла форматирования, а затем открывает эти файлы.|  
|[IBCPSession::BCPReadFmt &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|Считывает сведения о формате для каждого столбца из файла форматирования.|  
|[IBCPSession::BCPWriteFmt &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|Записывает в файл форматирования сведения о формате каждого из столбцов.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40; OLE DB &#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
