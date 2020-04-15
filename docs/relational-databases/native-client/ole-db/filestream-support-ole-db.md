---
title: Поддержка FILESTREAM (OLE DB) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: da09fc65de4be75798730fd0cc9785204a0c6917
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303715"
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Начиная [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и Native Client 10.0, OLE DB поддерживает расширенную функцию FILESTREAM. Для получения дополнительной информации [FILESTREAM Support](../../../relational-databases/native-client/features/filestream-support.md)об этой функции см. Примеры см. в статье [Filestream and OLE DB](../../../relational-databases/native-client-ole-db-how-to/filestream/filestream-and-ole-db.md) (Filestream и OLE DB).  
  
 Для отправки и получения значений **varbinary(max)** размером больше 2 ГБ, приложение использует для привязки параметров и результата **DBTYPE_IUNKNOWN**. Для получения параметров поставщик должен вызвать IUnknown::QueryInterface для ISequentialStream и для получения результатов, возвращающих ISequentialStream.  
  
 Для OLE DB проверка, связанная со значениями ISequentialStream, выполняется менее строго. Если *wType* имеет **DBTYPE_IUNKNOWN** в структуре **DBBINDING**, проверку длины можно отключить либо пропустив **DBPART_LENGTH** в *dwPart*, либо установив длину данных (при смещении *obLength* в буфере данных) на ~0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, которые передают данные, в основном IRowset::GetData, ICommand::Execute и IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
