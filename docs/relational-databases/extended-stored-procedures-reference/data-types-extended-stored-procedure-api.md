---
title: Типы данных (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e135e6706454fe1f03b4c7ab762e5234e1b7d35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064208"
---
# <a name="data-types-extended-stored-procedure-api"></a>Типы данных (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Для использования типов данных API расширенных хранимых процедур необходимо включить в программу файл заголовка Srv.h.  
  
|Тип данных|Тип данных SQL Server|Description|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|**binary**|тип данных **binary** , длина от 0 до 8000 байт.|  
|SRVBIGCHAR|**типа**|**символьный** тип данных, длина от 0 до 8000 байт.|  
|SRVBIGVARBINARY|**varbinary**|Данные типа **binary** с переменной длиной от 0 до 8000 байт.|  
|SRVBIGVARCHAR|**varchar**|Данные типа **character** с переменной длиной от 0 до 8000 байт.|  
|SRVBINARY|**binary**|тип данных **binary** .|  
|SRVBIT|**Версий**|тип данных **bit** .|  
|SRVBITN|**бит null**|тип данных **bit** , допустимые значения NULL.|  
|SRVCHAR|**типа**|**символьный** тип данных.|  
|SRVDATETIME|**datetime**|Тип данных **datetime** длиной 8 байт.|  
|SRVDATETIM4|**smalldatetime**|Тип данных **smalldatetime** длиной 4 байта.|  
|SRVDATETIMN|**DateTime null**|тип данных **smalldatetime** или **DateTime** , допустимые значения NULL.|  
|SRVDECIMAL|**Decimal**|тип данных **Decimal** .|  
|SRVDECIMALN|**десятичное значение null**|тип данных **Decimal** , допустимые значения NULL.|  
|SRVFLT4|**Real**|Тип данных **real** длиной 4 байта.|  
|SRVFLT8|**float**|Тип данных **float** длиной 8 байт.|  
|SRVFLTN|**real** &#124; **float NULL**|тип данных **Real** или **float** , допустимые значения NULL.|  
|SRVIMAGE|**Эскиз**|тип данных **Image** .|  
|SRVINT1|**tinyint**|Тип данных **tinyint** длиной 1 байт.|  
|SRVINT2|**smallint**|Тип данных **smallint** длиной 2 байта.|  
|SRVINT4|**int**|Тип данных **int** длиной 4 байта.|  
|SRVINTN|**tinyint** &#124; **smallint** &#124; **int NULL**|типы данных **tinyint**, **smallint**и **int** , значения null разрешены.|  
|SRVMONEY4|**smallmoney**|Тип данных **smallmoney** длиной 4 байта.|  
|SRVMONEY|**money**|Тип данных **money** длиной 8 байтов.|  
|SRVMONEYN|**money** &#124; **значение smallmoney NULL**|тип данных **smallmoney** или **money** , допустимые значения NULL.|  
|SRVNCHAR|**nchar**|Тип данных **character** (Юникод).|  
|SRVNTEXT|**ntext**|Тип данных **text** (Юникод).|  
|SRVNUMERIC|**ISNUMERIC**|**числовой** тип данных.|  
|SRVNUMERICN|**числовое значение null**|**числовой** тип данных, допустимые значения NULL.|  
|SRVNVARCHAR|**nvarchar**|Тип данных **character** (Юникод) переменной длины.|  
|SRVTEXT|**полнотекстовым**|тип данных **Text** .|  
|SRVVARBINARY|**varbinary**|Тип данных **binary** переменной длины.|  
|SRVVARCHAR|**varchar**|Тип данных **character** переменной длины.|  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
