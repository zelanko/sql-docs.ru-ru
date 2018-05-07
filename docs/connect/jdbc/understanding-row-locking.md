---
title: Основные сведения о блокировке строк | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdf5ca943ec4d823c8c568f0818a49c44f22cbe6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-row-locking"></a>Основные сведения о блокировке строк
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] блокировки строк. С помощью таких блокировок реализуется управление параллелизмом между несколькими пользователями, одновременно вносящими изменения в базу данных. По умолчанию управление транзакциями и блокировками ведется в рамках соединения. Например, если приложение открывает два соединения JDBC, то блокировки, установленные одним соединением, не могут совмещаться с другим соединением. Ни одно из соединений не может устанавливать блокировки, которые вызывают конфликт с блокировкам, удерживаемыми другим соединением.  
  
> [!NOTE]  
>  Если используется блокировка строк, то блокируются все строки в буфере выборки, поэтому задание очень большого размера выборки может отрицательно сказаться на параллелизме.  
  
 Блокировка обеспечивает целостность транзакций и согласованность базы данных. Блокировка не позволяет пользователям считывать данные, которые изменяются другими пользователями, а также исключает одновременное изменение одних и тех же данных несколькими пользователями. Если блокировка не применяется, то данные в базе данных могут утратить логическую верность, и запросы к этим данным могут давать непредвиденные результаты.  
  
> [!NOTE]  
>  Дополнительные сведения о блокировке строк в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе «блокировки в [!INCLUDE[ssDE](../../includes/ssde_md.md)]» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="see-also"></a>См. также  
 [Управление результирующими наборами с помощью драйвера JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
