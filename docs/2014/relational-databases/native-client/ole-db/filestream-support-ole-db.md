---
title: Поддержка FILESTREAM (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
ms.assetid: c2bd3dfd-6103-43d1-859e-8ed8d19c58d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad6aa7b55906e68dba6615140ef2c6afcc3efaa5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62668937"
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
  Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента 10,0, OLE DB поддерживает расширенную функцию FILESTREAM. Дополнительные сведения об этой функции см. в разделе [Поддержка FILESTREAM](../features/filestream-support.md). Примеры см. в статье [Filestream and OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md) (Filestream и OLE DB).  
  
 Для отправки и получения значений `varbinary(max)` размером больше 2 ГБ приложение использует для привязки параметров и результата тип `DBTYPE_IUNKNOWN`. Для получения параметров поставщик должен вызвать IUnknown::QueryInterface для ISequentialStream и для получения результатов, возвращающих ISequentialStream.  
  
 Для OLE DB проверка, связанная со значениями ISequentialStream, выполняется менее строго. Если *wType* находится `DBTYPE_IUNKNOWN` в `DBBINDING` структуре, проверка длины может быть отключена либо путем пропуска `DBPART_LENGTH` из *двпарт* , либо путем установки длины данных (в смещении *обленгс* в буфере данных) в ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, которые передают данные, в основном IRowset::GetData, ICommand::Execute и IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../sql-server-native-client-programming.md)  
  
  
