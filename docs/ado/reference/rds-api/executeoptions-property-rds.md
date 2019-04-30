---
title: Свойство ExecuteOptions (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ExecuteOptions property [ADO], VBScript example
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ac7ee6c1f996294c1f8aa353719deb11d698e47
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63308233"
---
# <a name="executeoptions-property-rds"></a>Свойство ExecuteOptions (служба удаленных рабочих столов)
Указывает, включена ли асинхронное выполнение.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Константа|Описание|  
|--------------|-----------------|  
|**adcExecSync**|Выполняет следующего обновления [записей](../../../ado/reference/ado-api/recordset-object-ado.md) синхронно.|  
|**adcExecAsync**|По умолчанию. Выполняет следующего обновления **записей** асинхронно.|  
  
> [!NOTE]
>  Каждый исполняемый файл, который использует эти константы необходимо предоставить объявления для них. Можно вырезать и вставить объявления констант из файла Adcvbs.inc, расположенный в папке установки по умолчанию для библиотеки служб удаленных рабочих СТОЛОВ.  
  
## <a name="remarks"></a>Примечания  
 Если **ExecuteOptions** присваивается **adcExecAsync**, то это асинхронно выполняет следующий **обновить** вызывать [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта **записей**.  
  
 Если вы попробуете вызвать [Сброс](../../../ado/reference/rds-api/reset-method-rds.md), [обновить](../../../ado/reference/rds-api/refresh-method-rds.md), [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), или [записей](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) тогда как другая асинхронная операция, которая может изменить [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта **записей** выполняется, возникает ошибка.  
  
 При возникновении ошибки во время асинхронной операции, **RDS. DataControl** объекта [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) значение изменяется с **adcReadyStateLoaded** для **adcReadyStateComplete**и  **Набор записей** значение свойства остается *ничего не*.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [ExecuteOptions и FetchOptions примеры свойств (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Метод Cancel (служба удаленных рабочих столов)](../../../ado/reference/rds-api/cancel-method-rds.md)


