---
title: PDO::Commit | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f30119d7fb8d2e1f23b719273738cc52cf3b7d00
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606334"
---
# <a name="pdocommit"></a>PDO::commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Отправляет в базу данных команды, выданные после вызова [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) , и возвращает подключение в режим автофиксации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDO::commit();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение true, если вызов метода выполнен успешно, в противном случае — значение false.  
  
## <a name="remarks"></a>Remarks  
PDO::commit не подвержен влиянию со стороны значения PDO::ATTR_AUTOCOMMIT (и не влияет на него).  
  
Пример использования PDO::commit см. в статье [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
