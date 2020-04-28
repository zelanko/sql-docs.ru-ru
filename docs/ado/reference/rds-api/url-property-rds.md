---
title: Свойство URL (служба удаленных рабочих столов) | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c88b8029ee5d96986cf9b366bd8faee53ca1393b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963227"
---
# <a name="url-property-rds"></a>Свойство URL (служба удаленных рабочих столов)
Указывает строку, содержащую относительный или абсолютный URL-адрес.  
  
 Свойство **URL** можно задать во время разработки в теге объекта [элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) DataObject или во время выполнения в коде скрипта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Параметры  
 *Server*  
 **Строковое** значение, содержащее допустимый URL-адрес.  
  
 *DataControl*  
 Объектная переменная, представляющая объект- **элемент управления** .  
  
## <a name="remarks"></a>Remarks  
 Как правило, URL-адрес определяет файл Active Server страницы (. ASP), который может создавать и возвращать [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md). Таким образом, пользователь может получить **набор записей** , не выполняя серверный объект [факта](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) на стороне сервера, или запрограммировать пользовательский бизнес-объект.  
  
 Если свойство **URL** задано, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) отправит изменения в расположение, указанное URL-адресом.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства URL (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


