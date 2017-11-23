---
title: "PDOStatement::getColumnMeta | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c43b41503fe74744a9c28c18210af6445a216a4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает метаданные для столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: отсчитываемый от нуля номер столбца, метаданные которого требуется извлечь (целое число).  
  
## <a name="return-value"></a>Возвращаемое значение  
Ассоциативный массив (ключ и значение), содержащий метаданные для столбца. Описание полей в массиве см. в разделе "Примечания".  
  
## <a name="remarks"></a>Замечания  
В следующей таблице перечислены поля в массиве, возвращенном getColumnMeta.  
  
|NAME|VALUES|  
|--------|----------|  
|native_type|Указывает тип PHP для столбца. Всегда строка.|  
|driver:decl_type|Указывает тип SQL, используемый для представления значения столбца в базе данных. Если столбец в результирующем наборе является результатом функции, это значение не возвращается PDOStatement::getColumnMeta.|  
|flags|Указывает флаги, установленные для этого столбца. Всегда равно 0.|  
|NAME|Указывает имя столбца в базе данных.|  
|table|Указывает имя таблицы, содержащей столбец в базе данных. Всегда пусто.|  
|len|Указывает длину столбца.|  
|precision|Указывает числовую точность этого столбца.|  
|pdo_type|Указывает тип этого столбца, представленный константами PDO::PARAM_*. Всегда PDO::PARAM_STR (2).|  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
