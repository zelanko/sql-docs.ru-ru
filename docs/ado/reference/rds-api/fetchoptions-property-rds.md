---
title: "Свойство FetchOptions (RDS) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- FetchOptions property [ADO]
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ca6ede3ae154cbb3b6e13038185e4a54a466009
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="fetchoptions-property-rds"></a>Свойство FetchOptions (RDS)
Указывает тип асинхронной доставки данных.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="setting-and-return-values"></a>Задание и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Константа|Description|  
|--------------|-----------------|  
|**adcFetchUpFront**|Все записи из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) будут выбраны до возврата управления в приложение. Полный **записей** извлечь, прежде чем приложение сможет выполнять никаких действий с ним.|  
|**adcFetchBackground**|Элемент управления может возвращать приложению сразу после первого пакета записей будут выбраны. Последующие чтение всех **записей** , попытки получения доступа к записи не выбраны в первого пакета будет отложено до фактического извлечения искомому записи, в какое время управление возвращается приложению.|  
|**adcFetchAsync**|По умолчанию. Управление немедленно возвращается приложению во время записи обрабатываются в фоновом режиме. Если приложение пытается прочитать запись, которая еще не выбраны, запись, наиболее близкое к искомому записи будут считываться и элемент управления возвращается немедленно, означает, что с текущего конца **записей** был достигнут. Например, вызов [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) переместит положения текущей записи на последнюю запись фактически выбрана, несмотря на то, что больше записей будет продолжать заполнение **записей**.|  
  
> [!NOTE]
>  Каждый клиентский исполняемый файл, который использует эти константы должен предоставить их объявления. Можно вырезать и вставить объявления констант из файла Adcvbs.inc, расположенный в папке установки по умолчанию для библиотеки служб удаленных рабочих СТОЛОВ.  
  
## <a name="remarks"></a>Замечания  
 Веб-приложения, обычно требуется использовать **adcFetchAsync** (значение по умолчанию), так как он обеспечивает более высокую производительность. В скомпилированных в клиентском приложении, обычно требуется использовать **adcFetchBackground**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [ExecuteOptions и пример свойства FetchOptions (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)



