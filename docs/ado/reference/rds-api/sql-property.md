---
title: Свойство SQL | Документы Microsoft
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c14edf35af65a9e9a64bbc89bb0cc9eb14a1d6a0
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288933"
---
# <a name="sql-property"></a>Свойство SQL
Указывает строку запроса, используемую для получения [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Можно задать **SQL** во время разработки в [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта тегов ОБЪЕКТОВ, или во время выполнения в коде сценария.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Параметры  
 *Строка запроса*  
 Объект **строка** значение, содержащее допустимый запрос данных SQL.  
  
 *DataControl*  
 Объектную переменную, которая представляет **RDS. DataControl** объекта.  
  
## <a name="remarks"></a>Примечания  
 Как правило, это инструкции SQL (с помощью диалекта сервера базы данных), такие как `"Select * from NewTitles"`. Чтобы обеспечить соответствие и обновить точно записей, обновляемых запрос должен содержать поля, отличный от Длинное двоичное поле или вычисляемого поля.  
  
 **SQL** свойство является необязательным, если пользовательских серверных бизнес-объект получает данные для клиента.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства SQL (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Свойство (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Метод запроса (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Обновить метод (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


