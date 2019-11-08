---
title: Поддержка FILESTREAM (OLE DB) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ff05424d9b8726f21c8c4aa2facd42b87961cc2
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73760875"
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10,0, OLE DB поддерживает расширенную функцию FILESTREAM. Дополнительные сведения об этой функции см. в разделе [Поддержка FILESTREAM](../../../relational-databases/native-client/features/filestream-support.md). Примеры см. в разделе [FileStream и OLE DB](../../../relational-databases/native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Чтобы отправлять и получать значения типа **varbinary (max)** , превышающие 2 ГБ, приложение использует **DBTYPE_IUNKNOWN** в привязках параметров и результатов. Для параметров поставщик должен вызвать IUnknown:: QueryInterface для ISequentialStream и для результатов, возвращающих ISequentialStream.  
  
 Для OLE DB проверка, связанная со значениями ISequentialStream, будет неослабленной. Если *wType* **DBTYPE_IUNKNOWN** в структуре **DBBINDING** , проверку длины можно отключить, опустив **DBPART_LENGTH** из *Двпарт* или задав длину данных (в смещении *обленгс* в данных). buffer) в ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, которые переносят данные, по основному методу IRowset:: GetData, ICommand:: Execute и IRowsetFastLoad:: InsertRow.  
  
## <a name="see-also"></a>См. также раздел  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
