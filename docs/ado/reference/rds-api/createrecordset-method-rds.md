---
title: Метод CreateRecordset (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
author: rothja
ms.author: jroth
ms.openlocfilehash: 53a391ccb25a32d628703543d95dc8e24668fcd5
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942496"
---
# <a name="createrecordset-method-rds"></a>Метод CreateRecordset (служба удаленных рабочих столов)
Создает пустой, отключенный [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Объект*  
 Объектная переменная, представляющая объект [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) DataObject или [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *колумнсинфос*  
 Массив **вариантов** атрибутов, определяющий каждый столбец в созданном **наборе записей** . Каждое определение столбца содержит массив из четырех обязательных атрибутов и один необязательный атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Имя|Имя заголовка столбца.|  
|Type|Целое число типа данных.|  
|Size|Целочисленное значение ширины в символах, независимо от типа данных.|  
|Допускает значения NULL|.|  
|Масштабирование (необязательно)|Этот необязательный атрибут определяет масштаб для числовых полей. Если это значение не указано, то числовые значения будут обрезаны до шкалы трех. На точность не влияет, но количество цифр после десятичной запятой будет усечено до трех.|  
  
 Затем набор массивов столбцов будет сгруппирован в массив, который определяет **набор записей**.  
  
## <a name="remarks"></a>Комментарии  
 Бизнес-объект на стороне сервера может заполнить результирующий **набор записей** данными из поставщика данных, не относящегося к OLE DB, например с помощью файла операционной системы, содержащего котировки котировок.  
  
 В следующей таблице перечислены значения [дататипинум](../../../ado/reference/ado-api/datatypeenum.md) , поддерживаемые методом **CreateRecordset** . В списке указывается номер ссылки, используемый для определения полей.  
  
 Каждый из типов данных имеет либо фиксированную длину, либо переменную длину. Типы фиксированной длины должны быть определены с размером-1, так как размер определяется заранее, а определение размера по-прежнему требуется. Типы данных переменной длины допускают размер от 1 до 32767.  
  
 Для некоторых типов данных переменных тип можно привести к типу, указанному в столбце подстановки. Подстановки не будут видны, пока не будет создан и заполнен **набор записей** . При необходимости можно проверить фактический тип данных.  
  
|Длина|Константа|Number|Подстановка|  
|------------|--------------|------------|------------------|  
|исправление|**adTinyInt**|16||  
|исправление|**adSmallInt**|2||  
|исправление|**adInteger**|3||  
|исправление|**adBigInt**|20||  
|исправление|**adUnsignedTinyInt**|17||  
|исправление|**adUnsignedSmallInt**|18||  
|исправление|**adUnsignedInt**|19||  
|исправление|**adUnsignedBigInt**|21||  
|исправление|**adSingle**|4||  
|исправление|**adDouble**|5||  
|исправление|**adCurrency**|6||  
|исправление|**adDecimal**|14||  
|исправление|**adNumeric**|131||  
|исправление|**adBoolean**|11||  
|исправление|**adError**|10||  
|исправление|**адгуид**|72||  
|исправление|**adDate**|7||  
|исправление|**adDBDate**|133||  
|исправление|**adDBTime**|134||  
|исправление|**аддбтиместамп**|135|7|  
|Переменная|**adBSTR**|8|130|  
|Переменная|**adChar**|129|200|  
|Переменная|**адварчар**|200||  
|Переменная|**adLongVarChar**|201|200|  
|Переменная|**adWChar**|130||  
|Переменная|**адварвчар**|202|130|  
|Переменная|**adLongVarWChar**|203|130|  
|Переменная|**adBinary**|128||  
|Переменная|**адварбинари**|204||  
|Переменная|**адлонгварбинари**|205|204|  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
    :::column-end:::
    :::column:::
        [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример метода CreateRecordset (Visual Basic)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Пример метода CreateRecordset (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [Метод CreateObject (служба удаленных рабочих столов)](../../../ado/reference/rds-api/createobject-method-rds.md)



