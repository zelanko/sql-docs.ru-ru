---
description: Свойство ReadyState (служба удаленных рабочих столов)
title: Свойство ReadyState (RDS) | Документация Майкрософт
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a7e27abfa2464f84e130d789db93a3d7606df21
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981485"
---
# <a name="readystate-property-rds"></a>Свойство ReadyState (служба удаленных рабочих столов)
Указывает ход выполнения объекта " [элемент управления](./datacontrol-object-rds.md) данными" при извлечении данных в объект [набора записей](../ado-api/recordset-object-ado.md) .  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**адкреадистателоадед**|Текущий запрос все еще выполняется и строки не выбраны. **Набор записей** объекта " **элемент управления** " недоступен для использования.|  
|**адкреадистатеинтерактиве**|Начальный набор строк, полученных текущим запросом, был сохранен в **наборе записей** объекта " **элемент управления** " и доступен для использования. Оставшиеся строки по-прежнему будут выбраны.|  
|**adcReadyStateComplete**|Все строки, полученные текущим запросом, были сохранены в **наборе записей** объекта " **элемент управления** " и доступны для использования.<br /><br /> Это состояние также будет существовать, если операция прервана из-за ошибки или если объект **набора записей** не инициализирован.|  
  
> [!NOTE]
>  Каждый исполняемый файл на стороне клиента, использующий эти константы, должен предоставлять объявления для них. Вы можете вырезать и вставить объявления констант из файла Адквбс. Inc, расположенного в папке установки по умолчанию для библиотеки RDS.  
  
## <a name="remarks"></a>Remarks  
 Используйте событие [onReadyStateChange](./onreadystatechange-event-rds.md) для отслеживания изменений в свойстве **ReadyState** во время асинхронной операции запроса. Это более эффективно, чем периодическая проверка значения свойства.  
  
 Если во время асинхронной операции возникает ошибка, свойство **ReadyState** меняется на **Адкреадистатекомплете**, свойство [State](../ado-api/state-property-ado.md) изменяется с **адстатиксекутинг** на **адстатеклосед**, а свойство [value](../ado-api/value-property-ado.md) объекта **Recordset** остается *пустым*.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ReadyState (VBScript)](./readystate-property-example-vbscript.md)   
 [Метод Cancel (RDS)](./cancel-method-rds.md)   
 [Свойство ExecuteOptions (служба удаленных рабочих столов)](./executeoptions-property-rds.md)