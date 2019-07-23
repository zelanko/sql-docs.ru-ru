---
title: 'PDOStatement:: OutAttribute | Документация Майкрософт'
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 014f679480caaabd42863d2551cfa4c25bbe94d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992981"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Получает значение предварительно определенного атрибута PDOStatement или пользовательского атрибута драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Параметры  
$*attribute*: целое число, одна из констант PDO::ATTR_* или PDO::SQLSRV_ATTR_\*. Поддерживаемые атрибуты — это атрибуты, которые можно задать с помощью [PDOStatement:: setAttribute](../../connect/php/pdostatement-setattribute.md), PDO:: SQLSRV_ATTR_DIRECT_QUERY (Дополнительные сведения см. [в разделе Выполнение прямых инструкций и подготовленная инструкция в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO: : ATTR_CURSOR и PDO:: SQLSRV_ATTR_CURSOR_SCROLL_TYPE (Дополнительные сведения см. в разделе [типы курсоров (драйвер PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Возвращаемое значение  
В случае успешного выполнения возвращает значение (смешанное) для предварительно заданного атрибута PDO или пользовательского атрибута драйвера. В неудачи возвращает значение NULL.  
  
## <a name="remarks"></a>Remarks  
Образец см. в статье [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
