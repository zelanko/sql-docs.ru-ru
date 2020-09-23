---
title: PDO::getAvailableDrivers
description: Справочник по API для функции PDO::getAvailableDrivers в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e43ef53820d24128d16ee0f0c7a5d6f1077ff6d2
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646624"
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
  
