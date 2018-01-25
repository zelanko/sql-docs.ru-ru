---
title: "DROP ФОРМАТА ВНЕШНЕГО файла (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 8cf9009b-59f9-4aac-bef1-dcf2cf0708b2
caps.latest.revision: "12"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 36795146dba75f7bf6a755c1c1ff700b9ed150cd
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="drop-external-file-format-transact-sql"></a>DROP ФОРМАТА ВНЕШНЕГО файла (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Удаляет PolyBase формата внешнего файла.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Drop an external file format  
DROP EXTERNAL FILE FORMAT external_file_format_name  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *external_file_format_name*  
 Имя формата внешнего файла для удаления.  
  
## <a name="metadata"></a>Метаданные  
 Чтобы просмотреть список, используйте форматы внешнего файла [sys.external_file_formats &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md) системного представления.  
  
```  
SELECT * FROM sys.external_file_formats;  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо изменить любой ФОРМАТ ВНЕШНЕГО файла.  
  
## <a name="general-remarks"></a>Общие замечания  
 Удаление формата внешних файлов не удаляет внешних данных.  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещаемой блокировки на объект формата внешнего файла.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-basic-syntax"></a>A. С помощью базовый синтаксис  
  
```  
DROP EXTERNAL FILE FORMAT myfileformat;  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  

