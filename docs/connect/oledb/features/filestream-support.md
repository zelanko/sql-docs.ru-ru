---
title: Поддержка FILESTREAM | Документы Microsoft
description: Поддержка FILESTREAM в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d9774e55a9366f99ad96fb5c2165abb3992f6e03
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], драйвер OLE DB для SQL Server поддерживает улучшенную функциональность FILESTREAM. Примеры см. в разделе [Filestream и OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM см. в разделе [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
При открытии подключения к базе данных **@@TEXTSIZE**  будет иметь значение -1 («неограниченный»), по умолчанию.  
  
Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
Дополнительные сведения см. в разделе [доступ к данным FILESTREAM с OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. ITableDefinition в OLE DB не может использоваться для создания столбца FILESTREAM.    
  
Чтобы создать столбцы FILESTREAM или обнаружить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать **is_filestream** столбец [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) представления каталога.  
  
Ниже представлен пример такого кода:  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Совместимость на низком уровне  
Если клиент был скомпилирован с помощью драйвера OLE DB для SQL Server, а приложение подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), затем **varbinary(max)** поведение будет совместимо с поведением представленные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение и возвращается предупреждение «строка данных справа усечение». 
  
Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **varbinary(max)** будут сопоставлены образ.  
  
## <a name="comments"></a>Комментарии
- Для отправки и получения **varbinary(max)** значения больше 2 ГБ, приложение использует **DBTYPE_IUNKNOWN** в привязках параметров и результатов. Для параметров поставщик должен вызывать IUnknown::QueryInterface для ISequentialStream и результатов, возвращающих ISequentialStream.  

-  Для OLE DB проверка связанные значения ISequentialStream выполняется менее строго. При *wType* — **DBTYPE_IUNKNOWN** в **DBBINDING** структуры, проверку длины можно отключить либо пропустив **DBPART_LENGTH** из *dwPart* или задав длину данных (в смещении *obLength* в буфере данных) для ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  Это изменение затрагивает все интерфейсы, передачи данных, часто запрашивается IRowset::GetData ICommand::Execute и IRowsetFastLoad::InsertRow.
 

## <a name="see-also"></a>См. также  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
