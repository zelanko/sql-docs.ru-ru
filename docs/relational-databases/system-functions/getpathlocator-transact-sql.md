---
title: GetPathLocator (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
author: rothja
ms.author: jroth
ms.openlocfilehash: 4cec490522f8bacc774213ec1af5cce1af0eefef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67910254"
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
 Путь к пространству имен в FileTable. Путь к пространству имен имеет тип **nvarchar (max)**.  
  
 Когда база данных входит в группу доступности Always On, функция **GetPathLocator** принимает имя виртуальной сети (VNN) или имя компьютера.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **hierarchyid**  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в статье [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="examples"></a>Примеры  
 Функцию **GetPathLocator** можно использовать при переносе файлов с файлового сервера в таблицу FileTable. В этом случае необходимо переместить файлы в FileTable, а затем заменить исходный путь UNC для каждого файла на путь UNC таблицы FileTable. Полный пример см. в разделе [Загрузка файлов в таблицы FileTable](../../relational-databases/blob/load-files-into-filetables.md).  
  
## <a name="see-also"></a>См. также  
 [Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
