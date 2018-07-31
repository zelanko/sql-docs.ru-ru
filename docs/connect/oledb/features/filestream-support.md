---
title: Поддержка FILESTREAM | Документация Майкрософт
description: Поддержка FILESTREAM в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
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
ms.openlocfilehash: b8c2b2c79ab9564fab1160a0434d7146a311a0f8
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106150"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Начиная с версии [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], драйвер OLE DB для SQL Server поддерживает улучшенную функциональность FILESTREAM. Примеры, см. в разделе [Filestream и OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM, см. в разделе [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
После открытия подключения к базе данных параметр **@@TEXTSIZE** устанавливается в значение –1 ("неограниченный") по умолчанию.  
  
Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
Дополнительные сведения см. в разделе [Доступ к данным FILESTREAM с помощью OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md).  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. Для создания столбца FILESTREAM невозможно использовать интерфейс ITableDefinition в OLE DB.    
  
Чтобы создать столбцы FILESTREAM или определить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать столбец **is_filestream** представления каталога [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).  
  
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
Если клиент был скомпилирован с помощью драйвера OLE DB для SQL Server, а приложение подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), затем **varbinary(max)** поведение будут совместимы с поведением представленные [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение, и будет возвращено сообщение "Усечение строковых данных справа". 
  
Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], значение **varbinary(max)** будет сопоставлено с изображением.  
  
## <a name="comments"></a>Комментарии
- Для отправки и получения **varbinary(max)** значения, размер которых превышает 2 ГБ, приложение использует **DBTYPE_IUNKNOWN** в привязки параметров и результата. Для параметров поставщик должен вызывать IUnknown::QueryInterface ISequentialStream и результаты, которые возвращают ISequentialStream.  

-  Для OLE DB проверка соответствующим значениям ISequentialStream будет снято еще. Когда *wType* — **DBTYPE_IUNKNOWN** в **DBBINDING** структуры, проверку длины можно отключить, убрав **DBPART_LENGTH** из *dwPart* или задав длину данных (по смещению *obLength* в буфере данных) к ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  Это изменение затрагивает все интерфейсы, которые передают данные, главным образом IRowset::GetData ICommand::Execute и IRowsetFastLoad::InsertRow.
 

## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
