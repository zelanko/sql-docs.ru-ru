---
title: Свойство URL-адрес (RDS) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: d5c1975e72a90defc15e4fcb41f0cfe44a714dc8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697197"
---
# <a name="url-property-rds"></a>Свойство URL (служба удаленных рабочих столов)
Указывает строку, которая содержит относительный или абсолютный URL-адрес.  
  
 Можно задать **URL-адрес** во время разработки в [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) ОБЪЕКТА тег или во время выполнения в коде сценария.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Параметры  
 *Server*  
 Объект **строка** значение, содержащее допустимый URL-адрес.  
  
 *DataControl*  
 Объектную переменную, которая представляет **DataControl** объекта.  
  
## <a name="remarks"></a>Примечания  
 Как правило, URL-адрес указывает файл ASP-страницу (.asp), который может создавать и возвращать [записей](../../../ado/reference/ado-api/recordset-object-ado.md). Таким образом, пользователь сможет получить **записей** без вызова на стороне сервера [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта или запрограммировать пользовательские бизнес-объекта.  
  
 Если **URL-адрес** свойство задано, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) будет отправить изменения в расположение, указанное в URL-адресом.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства URL (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


