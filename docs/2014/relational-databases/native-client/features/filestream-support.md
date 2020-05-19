---
title: Поддержка FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ab8ca7912db7607acbca716f733184ed57dc681e
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707295"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
  Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM см. в статье [FILESTREAM (SQL Server)](../../blob/filestream-sql-server.md).  
  
 После открытия подключения к базе данных параметр `@@TEXTSIZE` устанавливается в значение -1 («неограниченный») по умолчанию.  
  
 Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Поддержка FILESTREAM &#40;OLE DB&#41;](../ole-db/filestream-support-ole-db.md)  
  
-   [Поддержка FILESTREAM &#40;ODBC&#41;](../odbc/filestream-support-odbc.md)  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
 Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. Для создания столбца FILESTREAM невозможно использовать интерфейс ITableDefinition в OLE DB.  
  
 Функции каталога, такие как SQLColumns в ODBC, не сообщают о том, является ли столбец столбцом FILESTREAM.  
  
 Чтобы создать столбцы FILESTREAM или определить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать `is_filestream` Столбец представления каталога [sys. Columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) .  
  
 Ниже представлен пример такого кода:  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Совместимость на низком уровне  
 Если клиент был скомпилирован с использованием версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента, которая была включена в [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)] , `varbinary(max)` поведение будет совместимо с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] . Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение, и будет возвращено сообщение "Усечение строковых данных справа".  
  
 Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
 Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] собственного клиента, `varbinary(max)` будут сопоставлены с изображением.  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](sql-server-native-client-features.md)  
  
  
