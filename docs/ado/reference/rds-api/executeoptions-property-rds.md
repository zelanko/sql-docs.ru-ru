---
description: Свойство ExecuteOptions (служба удаленных рабочих столов)
title: Свойство Ексекутеоптионс (RDS) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 042a69dd679cf84e2ab26da77cda3c06d2abd94e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768313"
---
# <a name="executeoptions-property-rds"></a>Свойство ExecuteOptions (служба удаленных рабочих столов)
Указывает, включено ли асинхронное выполнение.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Константа|Описание|  
|--------------|-----------------|  
|**adcExecSync**|Синхронно выполняет следующее обновление [набора записей](../ado-api/recordset-object-ado.md) .|  
|**adcExecAsync**|По умолчанию. Асинхронно выполняет следующее обновление **набора записей** .|  
  
> [!NOTE]
>  Каждый исполняемый файл, использующий эти константы, должен предоставлять объявления для них. Вы можете вырезать и вставить объявления констант из файла Адквбс. Inc, расположенного в папке установки по умолчанию для библиотеки RDS.  
  
## <a name="remarks"></a>Remarks  
 Если для **ексекутеоптионс** задано значение **адцексекасинк**, то асинхронно выполняет следующий вызов **Refresh** в [RDS. ](./datacontrol-object-rds.md) **Набор записей**объекта данных.  
  
 При попытке вызвать метод [Reset](./reset-method-rds.md), [Refresh](./refresh-method-rds.md), [SubmitChanges](./submitchanges-method-rds.md), [CancelUpdate](../ado-api/cancelupdate-method-ado.md)или [Recordset](./recordset-sourcerecordset-properties-rds.md) , пока другая асинхронная операция может изменить [RDS. ](./datacontrol-object-rds.md) Выполняется **набор записей** объекта "элемент управления", возникает ошибка.  
  
 Если во время асинхронной операции возникает ошибка, то **RDS. ** Значение свойства [ReadyState](./readystate-property-rds.md) объекта "элемент управления **адкреадистателоадед** " изменяется с " **адкреадистатекомплете**" на "", а значение "свойство **набора записей** " остается *пустым*.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств Ексекутеоптионс и FetchOptions (VBScript)](./executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Метод Cancel (служба удаленных рабочих столов)](./cancel-method-rds.md)