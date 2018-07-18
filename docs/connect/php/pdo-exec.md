---
title: PDO::Exec | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca46ace5ee5e5c0c461687d1e84ef5e0072506e5
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308193"
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Подготавливает и выполняет инструкцию SQL в одном вызове функции, возвращая количество строк, затронутых этой инструкцией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>Параметры  
*$statement*: строка, содержащая инструкцию SQL для выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
Целое число, обозначающее количество затронутых строк.  
  
## <a name="remarks"></a>Примечания  
Если *$statement* содержит несколько инструкций SQL, количество затронутых строк указывается только для последней инструкции.  
  
PDO::exec не возвращает результаты для инструкции SELECT.  
  
Следующие атрибуты влияют на поведение PDO::exec:  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
Дополнительные сведения см. в статье [PDO::setAttribute](../../connect/php/pdo-setattribute.md). 
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример удаляет строки таблицы Table1, содержащие "xxxyy" в столбце col1. Затем пример сообщает, сколько строк было удалено.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
