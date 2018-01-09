---
title: "Поддержка FILESTREAM (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f526ae674729f17a1e0eac39885c39a4395a7561
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0, OLE DB поддерживает улучшенную функциональность FILESTREAM. Дополнительные сведения об этой функции см. в разделе [поддержка FILESTREAM](../../../relational-databases/native-client/features/filestream-support.md). Примеры см. в разделе [Filestream и OLE DB](../../../relational-databases/native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Для отправки и получения **varbinary(max)** значения больше 2 ГБ, приложение использует **DBTYPE_IUNKNOWN** в привязках параметров и результатов. Для параметров поставщик должен вызывать IUnknown::QueryInterface для ISequentialStream и результатов, возвращающих ISequentialStream.  
  
 Для OLE DB проверка связанные значения ISequentialStream выполняется менее строго. При *wType* — **DBTYPE_IUNKNOWN** в **DBBINDING** структуры, проверку длины можно отключить либо пропустив **DBPART_LENGTH** из *dwPart* или задав длину данных (в смещении *obLength* в буфере данных) для ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, передачи данных, часто запрашивается IRowset::GetData ICommand::Execute и IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
