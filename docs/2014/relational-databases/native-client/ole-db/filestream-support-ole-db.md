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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62668937"
---
# <a name="filestream-support-ole-db"></a>Поддержка FILESTREAM (OLE DB)
  Начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент версии 10.0, OLE DB поддерживает улучшенную функциональность FILESTREAM. Дополнительные сведения об этой функции см. в разделе [поддержка FILESTREAM](../features/filestream-support.md). Примеры, см. в разделе [Filestream и OLE DB](../../native-client-ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Для отправки и получения значений `varbinary(max)` размером больше 2 ГБ приложение использует для привязки параметров и результата тип `DBTYPE_IUNKNOWN`. Для параметров поставщик должен вызывать IUnknown::QueryInterface ISequentialStream и результаты, которые возвращают ISequentialStream.  
  
 Для OLE DB проверка соответствующим значениям ISequentialStream будет снято еще. Когда *wType* — `DBTYPE_IUNKNOWN` в `DBBINDING` структуры, проверку длины можно отключить, убрав `DBPART_LENGTH` из *dwPart* или задав длину данных (по смещению *obLength* в буфере данных) к ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  
  
 Это изменение затрагивает все интерфейсы, которые передают данные, главным образом IRowset::GetData ICommand::Execute и IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../sql-server-native-client-programming.md)  
  
  
