---
title: "Метод CreateRecordset (RDS) | Документы Microsoft"
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
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f5a273957b03cfb26e0f6d3f1b4aa563f9079e2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="createrecordset-method-rds"></a>Метод CreateRecordset (RDS)
Создает пустой, отключен [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Объект*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) или [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *ColumnsInfos*  
 Объект **Variant** массив атрибутов, который определяет каждый столбец в **записей** создан. Каждое определение столбца содержит массив из четырех необходимые атрибуты и один необязательный атрибут.  
  
|Attribute|Description|  
|---------------|-----------------|  
|Имя|Имя заголовка столбца.|  
|Тип|Целое число типа данных.|  
|Размер|Целое число от ширины в символах, независимо от типа данных.|  
|Допускает значения NULL|Логическое значение.|  
|Масштаб (необязательно)|Этот необязательный атрибут определяет масштаб для числовых полей. Если это значение не задано, числовые значения будет усечено до масштабом 3. Точность не затронуты, но количество цифр после десятичной запятой будет усечено до трех.|  
  
 Набор столбцов массивов, затем группируются в массив, который определяет **записей**.  
  
## <a name="remarks"></a>Замечания  
 Серверные бизнес-объекта, можно заполнить итоговый **записей** данными из не - поставщик данных OLE DB, такие как операционной системой файл содержащего биржевых котировок.  
  
 В следующей таблице перечислены [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значений, поддерживаемых **CreateRecordset** метод. Номер, указанный — это номер ссылки, используемый для определения полей.  
  
 Каждый из типов данных является фиксированной или переменной длины. Типы фиксированной длины должен быть определен с размером – 1, так как размер определяется и по-прежнему требуется определение размера. Типы данных с переменной длиной, позволяют размер от 1 до 32767.  
  
 Для некоторых типов данных переменной тип может быть преобразовано в тип, указанный в столбце подстановки. Вы не увидите после подстановки до **записей** создания. Затем можно искать реальный тип данных, при необходимости.  
  
|Длина|Константа|Количество|Подстановки|  
|------------|--------------|------------|------------------|  
|Фиксированный|**adTinyInt**|16||  
|Фиксированный|**adSmallInt**|2||  
|Фиксированный|**adInteger**|3||  
|Фиксированный|**adBigInt**|20||  
|Фиксированный|**adUnsignedTinyInt**|17||  
|Фиксированный|**adUnsignedSmallInt**|18||  
|Фиксированный|**adUnsignedInt**|19||  
|Фиксированный|**adUnsignedBigInt**|21||  
|Фиксированный|**adSingle**|4||  
|Фиксированный|**adDouble**|5||  
|Фиксированный|**adCurrency**|6||  
|Фиксированный|**adDecimal**|14||  
|Фиксированный|**adNumeric**|131||  
|Фиксированный|**adBoolean**|11||  
|Фиксированный|**adError**|10||  
|Фиксированный|**adGuid**|72||  
|Фиксированный|**adDate**|7||  
|Фиксированный|**adDBDate**|133||  
|Фиксированный|**adDBTime**|134||  
|Фиксированный|**adDBTimestamp**|135|7|  
|Переменная|**adBSTR**|8|130|  
|Переменная|**adChar**|129|200|  
|Переменная|**adVarChar**|200||  
|Переменная|**adLongVarChar**|201|200|  
|Переменная|**adWChar**|130||  
|Переменная|**adVarWChar**|202|130|  
|Переменная|**adLongVarWChar**|203|130|  
|Переменная|**adBinary**|128||  
|Переменная|**adVarBinary**|204||  
|Переменная|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример метода CreateRecordset (Visual Basic)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Пример метода CreateRecordset (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [Метод CreateObject (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)




