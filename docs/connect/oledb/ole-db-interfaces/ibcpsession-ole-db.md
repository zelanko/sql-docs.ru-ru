---
title: Интерфейс IBCPSession (OLE DB) | Документы Microsoft
description: Интерфейс IBCPSession (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e07dab3ad117f513545a38e488eb12349c72482a
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="ibcpsession-ole-db"></a>Интерфейс IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IBCPSession** интерфейс обеспечивает поддержку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] операций массового копирования. **IBCPSession** интерфейс, предоставленный в драйвер OLE DB для SQL Server в том же уровне, что сеансы. В драйвер OLE DB для SQL Server объекты источника данных являются фабриками объектов Session, и операции массового копирования указываются в свойстве соединения SSPROP_ENABLEBULKCOPY. Кроме того, свойство SSPROP_ENABLEFASTLOAD должно быть установлено в значение TRUE.  
  
 Вызов метода **IDBCreateSession::CreateSession** приведет к созданию объекта **BulkCopySession** . Все методы массового копирования, основанные на файлах, доступные через объект **IBCPSession** , можно вызывать с помощью этих объектов **IBCPSession** интерфейса **IBCPSession** .  
  
> [!NOTE]  
>  Драйвер OLE DB для SQL Server поддерживает операции на основе памяти массового копирования через [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) интерфейса.  
  
 Дополнительные сведения об использовании драйвера OLE DB для SQL Server для операций массового копирования см. в разделе [выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md).  
  
 Пример, демонстрирующий использование **IBCPSession** интерфейса см. в разделе [IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Метод|Описание|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|Создает привязку между переменными программы и столбцами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|Задает количество полей для привязки к столбцам в таблице [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Метод IBCPSession::BCPControl &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|Устанавливает параметры для операции массового копирования.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|Фиксирует оставшиеся строки для отправки в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|Выполняет операцию массового копирования.|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|Инициализирует структуру массового копирования, выполняет проверку ошибок, проверяет правильность имен файла данных и файла форматирования, а затем открывает эти файлы.|  
|[Метод IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|Считывает сведения о формате для каждого столбца из файла форматирования.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|Записывает в файл форматирования сведения о формате каждого из столбцов.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40; OLE DB &#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)  
  
  
