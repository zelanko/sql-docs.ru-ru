---
title: "Свойства сервера (RDS) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: RDS::IBindMgr21::Server
helpviewer_keywords: Server property [RDS]
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e1475b73658e9cbf5b1b1ebc393d2cf60bb6e5f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="server-property-rds"></a>Свойства сервера (RDS)
Указывает протокол, имя и обмен данными службы Internet Information Services (IIS).  
  
 Можно задать **сервера** во время разработки в теги ОБЪЕКТА[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) , во время выполнения в коде сценария или объекта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 **HTTP**  
  
 Синтаксис во время разработки  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 Синтаксис во время выполнения  
  
```  
  
DataControl  
.Server="http://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 Синтаксис во время разработки  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 Синтаксис во время выполнения  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 Синтаксис во время разработки  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 Синтаксис во время выполнения  
  
```  
  
DataControl.Server="computername"  
```  
  
 **В процессе**  
  
 Синтаксис во время разработки  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 Синтаксис во время выполнения  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>Параметры  
 *awebsrvr*или *computername*  
 Объект **строка** значение, содержащее Интернета или интрасети путь или имя компьютера, если сервер находится на удаленном компьютере, или пустая строка, если сервер находится на локальном компьютере.  
  
 *port*  
 Необязательно. Порт, используемый для подключения к серверу, на котором запущены службы IIS. Номер порта задается в Internet Explorer (на **представление** меню, нажмите кнопку **параметры**и выберите **подключения** вкладку) или в службах IIS.  
  
 *DataControl*  
 Объектную переменную, которая представляет **RDS. DataControl** объекта.  
  
## <a name="remarks"></a>Замечания  
 Сервер находится где **RDS. DataControl** обработки запроса (то есть запрос или обновление). По умолчанию, все запросы обрабатываются [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта, [MSDFMAP. Обработчик](../../../ado/guide/remote-data-service/datafactory-customization.md) компонента, и [MSDFMAP. INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md) файлу на указанном сервере. Следует помнить, что при изменении серверов для согласования параметров в старой и новой **MSDFMAP. INI** файлов. Проблемы совместимости может привести к запросы, которые завершаются успешно на одном сервере сбой на другом. Если свойство установлено в пустую строку «», эти объекты будут использоваться на локальном компьютере.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства сервера (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [Свойство (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Свойство SQL](../../../ado/reference/rds-api/sql-property.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


