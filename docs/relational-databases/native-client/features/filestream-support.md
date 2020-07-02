---
title: Поддержка FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 97ee05c8deb88efcd451eb55007983833d0b1879
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719678"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]

  Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM см. в статье [FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md).  
  
 При открытии подключения к базе данных значение ** \@ \@ TEXTSIZE** по умолчанию равно-1 ("неограниченно").  
  
 Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Поддержка FILESTREAM &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [Поддержка FILESTREAM &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
 Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. Для создания столбца FILESTREAM невозможно использовать интерфейс ITableDefinition в OLE DB.  
  
 Функции каталога, такие как SQLColumns в ODBC, не сообщают о том, является ли столбец столбцом FILESTREAM.  
  
 Чтобы создать столбцы FILESTREAM или определить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать столбец **is_filestream** представления каталога [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).  
  
 Ниже приведен пример:  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Совместимость на низком уровне  
 Если клиент был скомпилирован с использованием версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента, которая была включена в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] , а приложение подключается к [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , то поведение **varbinary (max)** будет совместимо с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] . Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение, и будет возвращено сообщение "Усечение строковых данных справа".  
  
 Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
 Для клиентов, использующих SQLOLEDB или других поставщиков, освобожденных до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента, тип **varbinary (max)** будет сопоставлен с изображением.  
  
## <a name="see-also"></a>См. также  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
