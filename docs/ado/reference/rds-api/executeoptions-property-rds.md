---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2ae55ec1fccbd491854fb8bff2daa215d38b20ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964188"
---
# <a name="executeoptions-property-rds"></a>Свойство ExecuteOptions (служба удаленных рабочих столов)
Указывает, включено ли асинхронное выполнение.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает одно из следующих значений.  
  
|Постоянно|Description|  
|--------------|-----------------|  
|**адцексексинк**|Синхронно выполняет следующее обновление [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .|  
|**адцексекасинк**|По умолчанию. Асинхронно выполняет следующее обновление **набора записей** .|  
  
> [!NOTE]
>  Каждый исполняемый файл, использующий эти константы, должен предоставлять объявления для них. Вы можете вырезать и вставить объявления констант из файла Адквбс. Inc, расположенного в папке установки по умолчанию для библиотеки RDS.  
  
## <a name="remarks"></a>Remarks  
 Если для **ексекутеоптионс** задано значение **адцексекасинк**, то асинхронно выполняет следующий вызов **Refresh** в [RDS. ](../../../ado/reference/rds-api/datacontrol-object-rds.md) **Набор записей**объекта данных.  
  
 При попытке вызвать метод [Reset](../../../ado/reference/rds-api/reset-method-rds.md), [Refresh](../../../ado/reference/rds-api/refresh-method-rds.md), [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)или [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) , пока другая асинхронная операция может изменить [RDS. ](../../../ado/reference/rds-api/datacontrol-object-rds.md)Выполняется **набор записей** объекта "элемент управления", возникает ошибка.  
  
 Если во время асинхронной операции возникает ошибка, то **RDS. **Значение свойства [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) объекта "элемент управления **адкреадистателоадед** " изменяется с " **адкреадистатекомплете**" на "", а значение "свойство **набора записей** " остается *пустым*.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств Ексекутеоптионс и FetchOptions (VBScript)](../../../ado/reference/rds-api/executeoptions-and-fetchoptions-properties-example-vbscript.md)   
 [Метод Cancel (служба удаленных рабочих столов)](../../../ado/reference/rds-api/cancel-method-rds.md)


