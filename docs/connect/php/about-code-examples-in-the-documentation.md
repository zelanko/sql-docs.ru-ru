---
title: Информация о примерах кода в документации | Документы Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d8de0d865584fc45f5da732b5bdf79c6edef650
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307473"
---
# <a name="about-code-examples-in-the-documentation"></a>Информация о примерах кода в документации
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>Примечания о примерах кода
Существует несколько аспектов, на которые необходимо обратить внимание при выполнении примеров кода из документации [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] :  
  
-   Почти во всех примерах предполагается, что SQL Server 2008 или более поздней версии и базы данных AdventureWorks установлены на локальном компьютере.  
  
    Сведения о том, как скачать бесплатные выпуски и пробные версии SQL Server см. в статье [SQL Server](http://go.microsoft.com/fwlink/?LinkID=120193).  
  
    Сведения о том, как загрузить и установить базу данных AdventureWorks см. в разделе [AdventureWorks страницы в репозитории Github образцы SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works).
  
-   Почти все примеры кода в этой документации предназначены для выполнения из командной строки, что позволяет автоматически тестировать все примеры кода. Сведения о том, как запустить PHP из командной строки, см. в статье [Использование PHP из командной строки](http://php.net/manual/en/features.commandline.php).  
  
-   Хотя примеры предназначены для запуска из командной строки, любой пример можно выполнить путем вызова из браузера без внесения изменений в скрипт. Для форматирования вывода хорошо, замените каждый элемент «\n» «\<\/br >» в каждом примере перед вызовом его из браузера.  
  
-   С целью сокращения объема рассматриваемого материала должная обработка ошибок реализована не во всех примерах. Рекомендуется проверять каждый вызов функции **sqlsrv** или метода PDO на наличие ошибок и обрабатывать их в соответствии с потребностями приложения.  
  
    Простой способ получения сведений об ошибках при возникновении ошибки заключается в том, чтобы выйти из скрипта с помощью следующей строки кода:  
  
    ```  
    die( print_r( sqlsrv_errors(), true));  
    ```  
  
    Или, если вы используете PDO,  
  
    ```  
    print_r ($stmt->errorInfo());  
    die();  
    ```  
  
    Дополнительные сведения об обработке ошибок и предупреждений см. в статье [Обработка ошибок и предупреждений](../../connect/php/handling-errors-and-warnings.md).  
  
## <a name="see-also"></a>См. также  
[Общие сведения о драйверы Майкрософт для PHP для SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)
  
