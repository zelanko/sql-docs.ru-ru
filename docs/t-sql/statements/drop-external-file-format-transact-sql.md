---
title: "DROP ФОРМАТА ВНЕШНЕГО файла (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8cf9009b-59f9-4aac-bef1-dcf2cf0708b2
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 9c30ce4ee5d28cb55b824827de6c89f8d673640c
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="drop-external-file-format-transact-sql"></a>DROP ФОРМАТА ВНЕШНЕГО файла (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

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
  
## <a name="permissions"></a>Permissions  
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
  
## <a name="see-also"></a>См. также:  
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  


