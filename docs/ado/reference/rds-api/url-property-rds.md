---
title: Свойство URL-адреса (RDS) | Документы Microsoft
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e798b7e4afd6ddf0e2238acff56adcff0a3cfb5c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="url-property-rds"></a>Свойство URL-адреса (RDS)
Указывает строку, содержащую относительный или абсолютный URL-адрес.  
  
 Можно задать **URL-адрес** во время разработки в [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) ОБЪЕКТА тега или во время выполнения в коде сценария.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Параметры  
 *Server*  
 Объект **строка** значение, которое содержит допустимый URL-адрес.  
  
 *DataControl*  
 Объектную переменную, которая представляет **DataControl** объекта.  
  
## <a name="remarks"></a>Замечания  
 Как правило, URL-адрес указывает файл Active Server Page (.asp), который может создавать и возвращать [записей](../../../ado/reference/ado-api/recordset-object-ado.md). Таким образом, пользователь может получить **записей** без вызова сервере [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) программы пользовательский бизнес-объект, или объект.  
  
 Если **URL-адрес** задал свойство [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) будет передать изменения в расположении, указанном в URL-адресе.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства URL (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


