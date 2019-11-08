---
title: Поддержка FILESTREAM | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4a60cb23aa48b071aa4f1db492cbd1629f38ab22
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761470"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о расширенной поддержке FILESTREAM см. [в &#40;разделе&#41;FILESTREAM SQL Server](../../../relational-databases/blob/filestream-sql-server.md).  
  
 После открытия подключения к базе данных параметр **@@TEXTSIZE** устанавливается в значение –1 ("неограниченный") по умолчанию.  
  
 Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [OLE DB поддержки &#40;FILESTREAM&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [Поддержка &#40;FILESTREAM в ODBC&#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
 Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. Для создания столбца FILESTREAM невозможно использовать интерфейс ITableDefinition в OLE DB.  
  
 Функции каталога, такие как SQLColumns в ODBC, не сообщают о том, является ли столбец столбцом FILESTREAM.  
  
 Чтобы создать столбцы FILESTREAM или определить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать столбец **is_filestream** представления каталога [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).  
  
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
 Если клиент был скомпилирован с использованием версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, которая была включена в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], и приложение подключается к [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], то поведение **varbinary (max)** будет совместимо с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение, и будет возвращено сообщение "Усечение строковых данных справа".  
  
 Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
 Для клиентов, использующих SQLOLEDB или других поставщиков, выпущенных до [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, **varbinary (max)** будет сопоставляться с изображением.  
  
## <a name="see-also"></a>См. также раздел  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
