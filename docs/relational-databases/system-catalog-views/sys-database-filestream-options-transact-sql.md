---
title: sys. database_filestream_options (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2cb185c2cec6bd2a7104384b3b75e14e2de4167f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85887934"
---
# <a name="sysdatabase_filestream_options-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает сведения об уровне нетранзакционного доступа к данным FILESTREAM в каждой из включенных таблиц FileTable. Содержит по одной строке для каждой базы данных в экземпляре SQL Server.  
  
 Дополнительные сведения о таблицах FileTable см. в разделе [Таблицы FileTable (SQL Server)](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|Столбец|Type|Описание|  
|------------|----------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных. Это значение уникально в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**directory_name**|**nvarchar(255)**|Каталог на уровне базы данных для всех пространств имен FileTable:|  
|**non_transacted_access**|**tinyint**|Включенный уровень нетранзакционного доступа к данным FILESTREAM. Уровень доступа задается параметром NON_TRANSACTED_ACCESS инструкции **Create Database** или **ALTER DATABASE** .<br /><br /> Этот параметр имеет одно из следующих значений:<br /><br /> 0 — не включено. Это значение по умолчанию. Этот уровень задается путем предоставления значения **Off** для параметра **NON_TRANSACTED_ACCESS** .<br /><br /> 1 — доступ только для чтения. Этот уровень задается путем предоставления значения **READ_ONLY** для параметра **NON_TRANSACTED_ACCESS** .<br /><br /> 3 — полный доступ. Этот уровень задается путем указания значения **Full** для параметра **NON_TRANSACTED_ACCESS** .<br /><br /> 5 — переход в состояние READONLY.<br /><br /> 6 — Переход в режим «Выкл.»|  
|**non_transacted_access_desc**|**nvarchar(60)**|Описание уровня нетранзакционного доступа, определенного в non_transacted_access.<br /><br /> Этот параметр имеет одно из следующих значений:<br /><br /> НЕТ — это значение по умолчанию.<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>См. также  
 [Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
