---
title: "Свойство ExecuteOptions (RDS) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56e631762097a140f722202a9eba6a304b66c0cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="executeoptions-property-rds"></a>Свойство ExecuteOptions (RDS)
Указывает, включен ли асинхронное выполнение.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Константа|Description|  
|--------------|-----------------|  
|**adcExecSync**|Выполняет следующего обновления [записей](../../../ado/reference/ado-api/recordset-object-ado.md) синхронно.|  
|**adcExecAsync**|По умолчанию. Выполняет следующего обновления **записей** асинхронно.|  
  
> [!NOTE]
>  Каждый исполняемый файл, который использует эти константы должен предоставить их объявления. Можно вырезать и вставить объявления констант, которые из файла Adcvbs.inc, расположенный в папке установки по умолчанию для библиотеки служб удаленных рабочих СТОЛОВ.  
  
## <a name="remarks"></a>Замечания  
 Если **ExecuteOptions** задано значение **adcExecAsync**, то это асинхронно выполняет следующий **обновления** вызывать [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта **записей**.  
  
 Если попытаться вызвать [Сброс](../../../ado/reference/rds-api/reset-method-rds.md), [обновление](../../../ado/reference/rds-api/refresh-method-rds.md), [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), или [записей](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) тогда как другая асинхронная операция, которая может изменить [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта **записей** выполняется, возникает ошибка.  
  
 При возникновении ошибки во время асинхронной операции, **RDS. DataControl** объекта [состояние готовности](../../../ado/reference/rds-api/readystate-property-rds.md) значение изменяется с **adcReadyStateLoaded** для **adcReadyStateComplete**и  **Набор записей** значение свойства остается *ничего не*.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [ExecuteOptions и пример свойства FetchOptions (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Метод Cancel (служба удаленных рабочих столов)](../../../ado/reference/rds-api/cancel-method-rds.md)


