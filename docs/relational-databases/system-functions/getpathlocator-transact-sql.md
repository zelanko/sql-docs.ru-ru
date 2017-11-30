---
title: "GetPathLocator (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs: TSQL
helpviewer_keywords: GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 732fbff8396430e415977c5a257d02731fa483eb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="getpathlocator-transact-sql"></a>GetPathLocator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение идентификатора path_locator для заданного файла или каталога в таблице FileTable.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GetPathLocator(filenamespace_path)  
```  
  
## <a name="arguments"></a>Аргументы  
 *filenamespace_path*  
 Путь к пространству имен в FileTable. Путь к пространству имен имеет тип **nvarchar(max)**.  
  
 Если база данных принадлежит к группе доступности Always On, то **GetPathLocator** функция принимает имя виртуальной сети (VNN) или имя компьютера.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **hierarchyid**  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в статье [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="examples"></a>Примеры  
 Можно использовать **GetPathLocator** работает, если выполняется перенос файлов с файлового сервера в filetable. В этом случае необходимо переместить файлы в FileTable, а затем заменить исходный путь UNC для каждого файла на путь UNC таблицы FileTable. Полный пример см. в разделе [загрузку файлов в таблицах Filetable](../../relational-databases/blob/load-files-into-filetables.md).  
  
## <a name="see-also"></a>См. также:  
 [Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
