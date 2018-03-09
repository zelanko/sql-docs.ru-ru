---
title: "Поддержка FILESTREAM | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ca2ec81cacec47dba4247f8c1c61ad2cf5d3d92
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM см. в разделе [FILESTREAM &#40; SQL Server &#41; ](../../../relational-databases/blob/filestream-sql-server.md).  
  
 При открытии подключения к базе данных **@@TEXTSIZE**  будет иметь значение -1 («неограниченный»), по умолчанию.  
  
 Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Поддержка FILESTREAM &#40; OLE DB &#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [Поддержка FILESTREAM &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
 Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. ITableDefinition в OLE DB не может использоваться для создания столбца FILESTREAM.  
  
 Функций каталога, например SQLColumns ODBC в будет не сообщают, является ли столбец столбцом FILESTREAM.  
  
 Чтобы создать столбцы FILESTREAM или обнаружить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать **is_filestream** столбец [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) представления каталога.  
  
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
 Если клиент был скомпилирован с помощью версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, которая прилагается [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], а приложение подключается к [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], **varbinary(max)** поведение будет совместимо с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение и возвращается предупреждение «строка данных справа усечение».  
  
 Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
 Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client **varbinary(max)** будут сопоставлены образ.  
  
## <a name="see-also"></a>См. также  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
