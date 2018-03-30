---
title: Поддержка FILESTREAM (OLE DB) | Документы Microsoft
description: Поддержка FILESTREAM (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7b1670cdda78f096ef776e7527910e71617c340
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и драйвер OLE DB для SQL Server, OLE DB поддерживает улучшенную функциональность FILESTREAM. Дополнительные сведения об этой функции см. в разделе [поддержка FILESTREAM](../../oledb/features/filestream-support.md). Примеры см. в разделе [Filestream и OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Для отправки и получения **varbinary(max)** значения больше 2 ГБ, приложение использует **DBTYPE_IUNKNOWN** в привязках параметров и результатов. Для параметров поставщик должен вызывать IUnknown::QueryInterface для ISequentialStream и результатов, возвращающих ISequentialStream.  
  
 Для OLE DB проверка связанные значения ISequentialStream выполняется менее строго. При *wType* — **DBTYPE_IUNKNOWN** в **DBBINDING** структуры, проверку длины можно отключить либо пропустив **DBPART_LENGTH** из *dwPart* или задав длину данных (в смещении *obLength* в буфере данных) для ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, передачи данных, часто запрашивается IRowset::GetData ICommand::Execute и IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server программирования](../../oledb/oledb-driver-for-sql-server-programming.md)  
  
  
