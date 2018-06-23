---
title: Поддержка FILESTREAM (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba270b26a5a290f5b5c6fdd2830f10b9bf695037
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096393"
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
  Начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0, OLE DB поддерживает улучшенную функциональность FILESTREAM. Дополнительные сведения об этой функции см. в разделе [поддержка FILESTREAM](../features/filestream-support.md). Примеры см. в разделе [Filestream и OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Для отправки и получения значений `varbinary(max)` размером больше 2 ГБ приложение использует для привязки параметров и результата тип `DBTYPE_IUNKNOWN`. Для параметров поставщик должен вызывать IUnknown::QueryInterface для ISequentialStream и результатов, возвращающих ISequentialStream.  
  
 Для OLE DB проверка связанные значения ISequentialStream выполняется менее строго. При *wType* — `DBTYPE_IUNKNOWN` в `DBBINDING` структуры, проверку длины можно отключить либо пропустив `DBPART_LENGTH` из *dwPart* или задав длину данных (в смещении *obLength* в буфере данных) для ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, передачи данных, часто запрашивается IRowset::GetData ICommand::Execute и IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../sql-server-native-client-programming.md)  
  
  