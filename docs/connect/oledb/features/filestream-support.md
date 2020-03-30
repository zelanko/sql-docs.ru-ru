---
title: Поддержка FILESTREAM | Документация Майкрософт
description: Поддержка FILESTREAM в драйвере OLE DB для SQL Server
ms.custom: ''
ms.date: 09/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: da67f050eba24ecf040124533c9d98c3f3f6bfec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "74056734"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], OLE DB Driver for SQL Server поддерживает улучшенную функциональность FILESTREAM. Примеры см. в статье [Filestream and OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md) (Filestream и OLE DB).  

Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM см. в статье [FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md).  
  
После открытия подключения к базе данных для параметра **\@\@TEXTSIZE** устанавливается значение –1 ("неограниченный") по умолчанию.  
  
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
Если ваш клиент скомпилирован с помощью OLE DB Driver for SQL Server, и приложение подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), тогда поведение **varbinary(max)** будет совместимо с поведением, введенным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение, и будет возвращено сообщение "Усечение строковых данных справа". 
  
Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], значение **varbinary(max)** будет сопоставлено с изображением.  
  
## <a name="comments"></a>Комментарии
- Для отправки и получения значений **varbinary(max)** размером больше 2 ГБ, приложение использует для привязки параметров и результата **DBTYPE_IUNKNOWN**. Для получения параметров поставщик должен вызвать IUnknown::QueryInterface для ISequentialStream и для получения результатов, возвращающих ISequentialStream.  

-  Для OLE DB проверка, связанная со значениями ISequentialStream, выполняется менее строго. Если *wType* имеет **DBTYPE_IUNKNOWN** в структуре **DBBINDING**, проверку длины можно отключить либо пропустив **DBPART_LENGTH** в *dwPart*, либо установив длину данных (при смещении *obLength* в буфере данных) на ~0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  Это изменение затрагивает все интерфейсы, которые передают данные, в основном IRowset::GetData, ICommand::Execute и IRowsetFastLoad::InsertRow.
 

## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
