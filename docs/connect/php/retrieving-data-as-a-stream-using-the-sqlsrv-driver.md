---
title: Извлечение данных в виде потока с помощью драйвера SQLSRV | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 17dc9129-04cd-430c-b5b3-82824116425d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d5d1d7e62709af773ca251a389c8cfaa4981ce58
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797044"
---
# <a name="retrieving-data-as-a-stream-using-the-sqlsrv-driver"></a>Извлечение данных в виде потока с помощью драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлечение данных в виде потока доступно только в драйвере SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] и недоступно в драйвере PDO_SQLSRV.  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] использует преимущества потоков для извлечения больших объемов данных. Статьи, представленные в данном разделе, содержат сведения о том, как извлечь данные в виде потока.  
  
Ниже представлена обобщенная процедура извлечения данных в виде потока:  
  
1.  Подготовка и выполнение запроса Transact-SQL с [sqlsrv_query](../../connect/php/sqlsrv-query.md) или сочетанием [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
2.  Используйте [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) для перемещения на следующую строку в результирующем наборе.  
  
3.  Используйте [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) для извлечения полей из строки. Укажите, что данные следует извлечь в виде потока, используя **SQLSRV_PHPTYPE_STREAM(<encoding>)** в качестве третьего параметра в вызове функции. В этой таблице перечислены константы, используемые для задания кодировок и их описаний.  
  
    |Константа SQLSRV|Описание|  
    |-------------------|---------------|  
    |SQLSRV_ENC_BINARY|Данные возвращаются в виде потока необработанных байтов с сервера без применения кодировки или преобразования.|  
    |SQLSRV_ENC_CHAR|Данные возвращаются в виде 8-битовых символов, как указано в кодовой странице языкового стандарта Windows, установленного в системе. Для всех многобайтовых символов или символов, не соответствующих этой кодовой странице, подставляется однобайтовый символ вопросительного знака (?).|  
  
> [!NOTE]  
> Некоторые типы данных по умолчанию возвращаются в виде потоков. Дополнительные сведения см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|---------|---------------|  
|[Типы данных, поддерживающие потоки с помощью драйвера SQLSRV](../../connect/php/data-types-with-stream-support-using-the-sqlsrv-driver.md)|Содержит список типов данных SQL Server, которые можно извлечь как потоки.|  
|[Практическое руководство. Извлечение символьных данных в виде потока с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md)|Демонстрирует, как извлекать символьные данные в виде потока.|  
|[Практическое руководство. Извлечение двоичных данных в виде потока с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver.md)|Демонстрирует, как извлекать двоичные данные в виде потока.|  
  
## <a name="see-also"></a>См. также:  
[Извлечение данных](../../connect/php/retrieving-data.md)

[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
  
