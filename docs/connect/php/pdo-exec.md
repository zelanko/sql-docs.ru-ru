---
title: PDO::Exec | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
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
ms.openlocfilehash: 205d07a7c64573bf970ebda1fc32950b7b362e37
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
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
  
