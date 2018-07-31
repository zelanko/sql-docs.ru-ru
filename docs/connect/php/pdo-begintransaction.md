---
title: PDO::beginTransaction | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48b5d1343a941904280c33f5a983be944c751f2f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020892"
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Отключает режим автофиксации и начинает транзакцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение true, если вызов метода выполнен успешно, в противном случае — значение false.  
  
## <a name="remarks"></a>Remarks  
Транзакция, начавшаяся с PDO::beginTransaction, заканчивается, когда вызывается [PDO::commit](../../connect/php/pdo-commit.md) или [PDO::rollback](../../connect/php/pdo-rollback.md).  
  
PDO::beginTransaction не подвержен влиянию со стороны значения PDO::ATTR_AUTOCOMMIT (и не влияет на него).  
  
Вы не можете вызвать PDO::beginTransaction до завершения предыдущего PDO::beginTransaction с PDO::rollback или PDO::commit.  
  
Если этот метод завершается ошибкой, подключение возвращается в режим автофиксации.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Следующий пример использует базу данных с именем Test и таблицу с именем Table1. Он запускает транзакцию, а затем выдает команды на добавление двух строк, после чего удаляет одну строку. Команды отправляются в базу данных, а транзакция явно завершается с `PDO::commit`.  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
