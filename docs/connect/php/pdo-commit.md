---
title: PDO::commit
description: Справочник по API для функции PDO::commit в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94e42cb5fccba7d69025de85b0247f7a4c065c03
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646194"
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
  
