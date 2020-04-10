---
title: PDO::getAvailableDrivers | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a9b24f4f8d0481ebf127a1619968b2c88c9e1d0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919291"
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает массив драйверов PDO в вашей установке PHP.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
Массив со списком драйверов PDO.  
  
## <a name="remarks"></a>Remarks  
Имя драйвера PDO используется в PDO::__construct, чтобы создать экземпляр PDO.  
  
PDO::getAvailableDrivers не обязательно должен быть реализован с помощью драйверов PHP. Дополнительные сведения об этом методе см. в документации по PHP.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
