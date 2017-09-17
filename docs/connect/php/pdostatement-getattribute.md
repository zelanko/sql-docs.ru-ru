---
title: "PDOStatement::getAttribute | Документы Microsoft"
ms.custom: 
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef6cddea6637104695435db5ba429d08faf38050
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Получает значение предварительно определенного атрибута PDOStatement или пользовательского атрибута драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Параметры  
$*атрибут*: целое число, одна из констант PDO::ATTR_ * или PDO::SQLSRV_ATTR_\* константы. Поддерживаются атрибуты, которые можно задать с помощью [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), PDO::SQLSRV_ATTR_DIRECT_QUERY (Дополнительные сведения см. в разделе [выполнение прямых и подготовленных инструкций в Драйвер PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO::ATTR_CURSOR и PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE (Дополнительные сведения см. в разделе [типы курсоров (драйвер PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Возвращаемое значение  
В случае успешного выполнения возвращает значение (смешанное) для предварительно заданного атрибута PDO или пользовательского атрибута драйвера. В неудачи возвращает значение NULL.  
  
## <a name="remarks"></a>Замечания  
Образец см. в статье [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

