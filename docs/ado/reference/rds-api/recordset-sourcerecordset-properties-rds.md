---
description: Свойства Recordset и SourceRecordset (служба удаленных рабочих столов)
title: Набор записей, свойства Саурцерекордсет (RDS) | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 27b6cf791b3b980000662f2073280d53f24aeaa1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981435"
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Свойства Recordset и SourceRecordset (служба удаленных рабочих столов)
Указывает объект **набора записей** , возвращенный из пользовательского бизнес-объекта.  
  
 Область **применения:** [объект элемента управления (RDS)](./datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](./datacontrol-object-rds.md) .  
  
 *набор записей*  
 Объектная переменная, представляющая объект **набора записей** .  
  
## <a name="remarks"></a>Remarks  
 Свойству **саурцерекордсет** можно присвоить набор [записей](../ado-api/recordset-object-ado.md) , возвращаемый из пользовательского бизнес-объекта.  
  
 Эти свойства позволяют приложению обрабатывать процесс привязки с помощью пользовательского процесса. Они получают набор строк, заключенный в **набор записей** , чтобы можно было напрямую взаимодействовать с **набором записей**, выполняя такие действия, как установка свойств или перебор **набора записей**.  
  
 Можно задать свойство **саурцерекордсет** или прочитать свойство **Recordset** во время выполнения в коде скрипта.  
  
 **Саурцерекордсет** — это свойство, доступное только для записи, в отличие от свойства **Recordset** , которое является свойством только для чтения.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств Recordset и Саурцерекордсет (VBScript)](./recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [Метод CreateRecordset (RDS)](./createrecordset-method-rds.md)   
 [Метод Query (служба удаленных рабочих столов)](./query-method-rds.md)