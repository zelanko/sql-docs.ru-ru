---
title: Свойство SQL | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
author: rothja
ms.author: jroth
ms.openlocfilehash: eb860ed19386b73d90fc26dab8fa96f4b9672a73
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750731"
---
# <a name="sql-property"></a>Свойство SQL
Указывает строку запроса, используемую для получения [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Свойство **SQL** можно задать во время разработки в [RDS. Теги объекта элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) DataObject или во время выполнения в коде скрипта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Параметры  
 *QueryString*  
 **Строковое** значение, содержащее допустимый запрос данных SQL.  
  
 *DataControl*  
 Объектная переменная, представляющая **RDS. Объект элемента управления** .  
  
## <a name="remarks"></a>Remarks  
 Как правило, это инструкция SQL (с использованием диалекта сервера базы данных), например `"Select * from NewTitles"` . Чтобы гарантировать точное сопоставление и обновление записей, обновляемый запрос должен содержать поле, отличное от длинного бинарного поля или вычисленного поля.  
  
 Свойство **SQL** является необязательным, если пользовательский бизнес-объект на стороне сервера получает данные для клиента.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства SQL (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Свойство Connect (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Метод query (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Метод Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


