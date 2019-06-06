---
title: sys.fn_helpcollations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_helpcollations
- fn_helpcollations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_helpcollations function
- collations [SQL Server], supported
- fn_helpcollations function
ms.assetid: b5082e81-1fee-4e2c-b567-5412eaee41c1
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 157cb3b24d04337c4949e3d6cfe38337895b3bea
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719426"
---
# <a name="sysfnhelpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)

[!INCLUDE[appliesto-ss-asdb-xxxx-pdw-md](../../includes/appliesto-ss-asdb-xxxx-pdw-md.md)]

  Возвращает список всех поддерживаемых параметров сортировки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>Возвращаемые таблицы

 **fn_helpcollations** возвращает следующую информацию.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Имя|**sysname**|Имя стандартных параметров сортировки|  
|Описание|**nvarchar(1000)**|Описание параметров сортировки|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает параметры сортировки Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также поддерживает ограниченное число (< 80) из параметров сортировки вызван [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметры сортировки, которые были разработаны до появления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаемые параметры сортировки Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметры сортировки по-прежнему поддерживаются для обеспечения обратной совместимости, но не должны использоваться для новых разработок. Дополнительные сведения о параметрах сортировки Windows см. в статье [Имя параметров сортировки Windows (Transact-SQL)](../../t-sql/statements/windows-collation-name-transact-sql.md). Дополнительные сведения о параметрах сортировки см. в разделе [Поддержка параметров сортировки и Юникода](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Примеры

 Следующий код возвращает имена всех параметров сортировки с двоичной сортировкой, начинающихся с буквы `L`.  
  
```sql  
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name like 'L%' AND Description LIKE '% binary sort';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Name                   Description  
 -------------------    ------------------------------------  
 Lao_100_BIN            Lao-100, binary sort  
 Latin1_General_BIN     Latin1-General, binary sort  
 Latin1_General_100_BIN Latin1-General-100, binary sort  
 Latvian_BIN            Latvian, binary sort  
 Latvian_100_BIN        Latvian-100, binary sort  
 Lithuanian_BIN         Lithuanian, binary sort  
 Lithuanian_100_BIN     Lithuanian-100, binary sort  
  
 (7 row(s) affected)  
 ```
  
## <a name="see-also"></a>См. также

[COLLATE (Transact-SQL)](~/t-sql/statements/collations.md)   
[COLLATIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Поддержка параметров сортировки базы данных для хранилища данных SQL Azure](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  