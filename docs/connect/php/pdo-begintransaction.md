---
title: "PDO::beginTransaction | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6c65de9c08dd4d92480c855378516850814ecd6b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
## <a name="remarks"></a>Замечания  
Транзакции, начавшиеся с PDO::beginTransaction, заканчиваются при вызове [PDO::commit](../../connect/php/pdo-commit.md) или [PDO::rollback](../../connect/php/pdo-rollback.md) .  
  
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
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

