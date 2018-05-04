---
title: PDO::ROLLBACK | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d918c1e3-1be0-4001-b3b0-000db6d9e8b8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc0e1aa5be08c28c4f84621d940a52e1c3719a79
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="pdorollback"></a>PDO::rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Отменяет команды базы данных, выданные после вызова [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) , и возвращает подключение в режим автофиксации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDO::rollBack ();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение true, если вызов метода выполнен успешно, в противном случае — значение false.  
  
## <a name="remarks"></a>Замечания  
PDO::rollback не подвержен влиянию со стороны значения PDO::ATTR_AUTOCOMMIT (и не влияет на него).  
  
Пример использования PDO::rollback см. в статье [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>См. также  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
