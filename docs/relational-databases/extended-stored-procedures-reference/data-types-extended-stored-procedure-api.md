---
title: Типы данных (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0e703c80db732560a45db72d8f8c0bf2a2ce21fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32938349"
---
# <a name="data-types-extended-stored-procedure-api"></a>Типы данных (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Для использования типов данных API расширенных хранимых процедур необходимо включить в программу файл заголовка Srv.h.  
  
|Тип данных|Тип данных SQL Server|Description|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|**binary**|Данные типа **binary** с длиной от 0 до 8000 байт.|  
|SRVBIGCHAR|**char**|Данные типа **character** с длиной от 0 до 8000 байт.|  
|SRVBIGVARBINARY|**varbinary**|Данные типа **binary** с переменной длиной от 0 до 8000 байт.|  
|SRVBIGVARCHAR|**varchar**|Данные типа **character** с переменной длиной от 0 до 8000 байт.|  
|SRVBINARY|**binary**|Тип данных **binary**.|  
|SRVBIT|**Bit**|Тип данных **bit**.|  
|SRVBITN|**bit null**|Данные типа **bit**, значения NULL допускаются.|  
|SRVCHAR|**char**|Тип данных **character**.|  
|SRVDATETIME|**datetime**|Тип данных **datetime** длиной 8 байт.|  
|SRVDATETIM4|**smalldatetime**|Тип данных **smalldatetime** длиной 4 байта.|  
|SRVDATETIMN|**datetime null**|Данные типа **smalldatetime** или **datetime**, значения NULL допускаются.|  
|SRVDECIMAL|**decimal**|Тип данных **decimal**.|  
|SRVDECIMALN|**decimal null**|Данные типа **decimal**, значения NULL допускаются.|  
|SRVFLT4|**real**|Тип данных **real** длиной 4 байта.|  
|SRVFLT8|**float**|Тип данных **float** длиной 8 байт.|  
|SRVFLTN|**real** &#124; **float null**|Данные типа **real** или **float**, значения NULL допускаются.|  
|SRVIMAGE|**image**|Тип данных **image**.|  
|SRVINT1|**tinyint**|Тип данных **tinyint** длиной 1 байт.|  
|SRVINT2|**smallint**|Тип данных **smallint** длиной 2 байта.|  
|SRVINT4|**int**|Тип данных **int** длиной 4 байта.|  
|SRVINTN|**tinyint** &#124; **smallint** &#124; **int null**|Данные типа **tinyint**, **smallint** или **int**, значения NULL допускаются.|  
|SRVMONEY4|**smallmoney**|Тип данных **smallmoney** длиной 4 байта.|  
|SRVMONEY|**money**|Тип данных **money** длиной 8 байтов.|  
|SRVMONEYN|**money** &#124; **smallmoney null**|Данные типа **smallmoney** или **money**, значения NULL допускаются.|  
|SRVNCHAR|**nchar**|Тип данных **character** (Юникод).|  
|SRVNTEXT|**ntext**|Тип данных **text** (Юникод).|  
|SRVNUMERIC|**numeric**|Тип данных **numeric**.|  
|SRVNUMERICN|**numeric null**|Данные типа **numeric**, значения NULL допускаются.|  
|SRVNVARCHAR|**nvarchar**|Тип данных **character** (Юникод) переменной длины.|  
|SRVTEXT|**text**|Тип данных **text**.|  
|SRVVARBINARY|**varbinary**|Тип данных **binary** переменной длины.|  
|SRVVARCHAR|**varchar**|Тип данных **character** переменной длины.|  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
