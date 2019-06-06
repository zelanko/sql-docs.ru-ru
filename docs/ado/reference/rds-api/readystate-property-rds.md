---
title: Свойство ReadyState (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ReadyState property [ADO]
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e71447143e08ebf117b6fe0eab002569ec48d020
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694877"
---
# <a name="readystate-property-rds"></a>Свойство ReadyState (служба удаленных рабочих столов)
Индикатор выполнения [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) как оно извлекает данные в его [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**adcReadyStateLoaded**|Текущий запрос по-прежнему выполняется и никакие строки не будут выбраны. **DataControl** объекта **записей** недоступен для использования.|  
|**adcReadyStateInteractive**|Начальный набор строк, полученных для текущего запроса будет сохранен в **DataControl** объекта **записей** и доступны для использования. По-прежнему осуществляется выборка оставшихся строк.|  
|**adcReadyStateComplete**|Все строки, полученные для текущего запроса, сохраненные в **DataControl** объекта **записей** и доступны для использования.<br /><br /> Это состояние также будет существовать, если операция прервана из-за ошибки или **записей** объект не инициализирован.|  
  
> [!NOTE]
>  Каждый клиентский исполняемый файл, который использует эти константы необходимо предоставить объявления для них. Можно вырезать и вставить объявления констант из файла Adcvbs.inc, расположенный в папке установки по умолчанию для библиотеки служб удаленных рабочих СТОЛОВ.  
  
## <a name="remarks"></a>Примечания  
 Используйте [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) событий для отслеживания изменений в **ReadyState** свойство во время асинхронной операции запроса. Это более эффективно, чем периодически проверяя значение свойства.  
  
 При возникновении ошибки во время асинхронной операции, **ReadyState** изменения свойств **adcReadyStateComplete**, [состояние](../../../ado/reference/ado-api/state-property-ado.md) свойство меняется с **adStateExecuting** для **adStateClosed**и **записей** объект [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство остается *Nothing* .  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ReadyState (VBScript)](../../../ado/reference/rds-api/readystate-property-example-vbscript.md)   
 [Метод Cancel (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Свойство ExecuteOptions (служба удаленных рабочих столов)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


