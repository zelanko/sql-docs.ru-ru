---
title: Поддержка FILESTREAM | Документация Майкрософт
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
ms.openlocfilehash: a548cfda44d40ba7ac37aaf4465c589c7256ffe7
ms.sourcegitcommit: 5a61854ddcd2c61bb6da30ccad68f0ad90da0c96
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70978059"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], Драйвер OLE DB для SQL Server поддерживает расширенную функцию FILESTREAM. Примеры см. в разделе [FileStream и OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о расширенной поддержке FILESTREAM см. [в &#40;разделе&#41;FILESTREAM SQL Server](../../../relational-databases/blob/filestream-sql-server.md).  
  
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
Если клиент был скомпилирован с помощью OLE DB драйвера для SQL Server и приложение подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] через [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), то поведение **varbinary (max)** будет совместимо с поведением, представленным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение, и будет возвращено сообщение "Усечение строковых данных справа". 
  
Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], значение **varbinary(max)** будет сопоставлено с изображением.  
  
## <a name="comments"></a>Комментарии
- Для отправки и получения значений типа **varbinary (max)** , превышающих 2 ГБ, приложение использует **DBTYPE_IUNKNOWN** в привязках параметров и результатов. Для параметров поставщик должен вызвать IUnknown:: QueryInterface для ISequentialStream и для результатов, возвращающих ISequentialStream.  

-  Для OLE DB проверка, связанная со значениями ISequentialStream, будет неослабленной. Если *WType* **DBTYPE_IUNKNOWN** в структуре **DBBINDING** , проверку длины можно отключить, опустив **DBPART_LENGTH** из *Двпарт* или задав длину данных (в смещении *обленгс* в данных). buffer) в ~ 0. В этом случае поставщик не будет проверять длину значения, а запросит и возвратит все данные, которые можно получить по потоку. Это изменение относится ко всем типам больших объектов (LOB) и XML, но только при подключении к серверу [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий. Это предоставляет разработчикам большую гибкость, в то же время поддерживая согласованность и обратную совместимость с существующими приложениями и серверами предыдущих версий.  Это изменение затрагивает все интерфейсы, которые переносят данные, по основному методу IRowset:: GetData, ICommand:: Execute и IRowsetFastLoad:: InsertRow.
 

## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
