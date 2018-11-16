---
title: Пример метода CreateRecordset (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b376924dfb1833165a1f40ecfd1487c49eb2dcb
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604624"
---
# <a name="createrecordset-method-rds"></a>Метод CreateRecordset (служба удаленных рабочих столов)
Создает пустой, отключен [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Объект*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) или [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *ColumnsInfos*  
 Объект **Variant** массив атрибутов, который определяет каждый столбец в **записей** создан. Каждое определение столбца содержит массив из четырех необходимых атрибутов и один необязательный атрибут.  
  
|attribute|Описание|  
|---------------|-----------------|  
|Имя|Имя заголовка столбца.|  
|Тип|Целое число типа данных.|  
|Размер|Целое число от ширины в символах, независимо от типа данных.|  
|Допускает значения NULL|Логическое значение.|  
|Масштаб (необязательно)|Этот необязательный атрибут определяет масштаб для числовых полей. Если это значение не указано, числовые значения будут усечены масштабом, равным трем. Не влияет на точность, но количество цифр после десятичной запятой будет усечено до трех.|  
  
 Набор массивов столбец, затем группируются в массиве, который определяет **записей**.  
  
## <a name="remarks"></a>Примечания  
 На стороне сервера бизнес-объект можно заполнить итоговый **записей** с данными из не - поставщик данных OLE DB, такие как операционная система файл содержащего котировки акций.  
  
 В следующей таблице перечислены [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значений, поддерживаемых **CreateRecordset** метод. Номер, указанный является справочный номер, используемый для определения полей.  
  
 Каждый из типов данных является фиксированной или переменной длины. Типы фиксированной длины должен быть определен с размером равно – 1, так как размер определяется предварительно и определение размера по-прежнему требуется. Типы данных переменной длины позволяют размер от 1 до 32767.  
  
 Для некоторых типов данных переменной тип может быть преобразован в тип, указаны в столбце подстановки. Вы не увидите подстановок до после **записей** создания. Затем вы можете проверить реальный тип данных, при необходимости.  
  
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
|[Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример метода CreateRecordset (Visual Basic)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [Пример метода CreateRecordset (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [Метод CreateObject (служба удаленных рабочих столов)](../../../ado/reference/rds-api/createobject-method-rds.md)



