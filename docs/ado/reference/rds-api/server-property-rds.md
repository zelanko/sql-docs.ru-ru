---
title: Свойства сервера (RDS) | Документация Майкрософт
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- RDS::IBindMgr21::Server
helpviewer_keywords:
- Server property [RDS]
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: add581048739a6ba12dc046d2f9362816b661687
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680626"
---
# <a name="server-property-rds"></a>Свойство Server (служба удаленных рабочих столов)
Указывает протокол, имя и обмен данными Internet Information Services (IIS).  
  
 Можно задать **Server** во время разработки в теги ОБЪЕКТА[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта, или во время выполнения в коде сценария.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
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
 Объект **строка** значение, содержащее Интернета или интрасети путь или имя компьютера, если сервер выполняется на удаленном компьютере; или пустая строка, если сервер выполняется на локальном компьютере.  
  
 *port*  
 Необязательный параметр. Порт, используемый для подключения к серверу, на котором запущены службы IIS. Номер порта задается в Internet Explorer (на **представление** меню, нажмите кнопку **параметры**, а затем выберите **подключения** вкладку) или в службах IIS.  
  
 *DataControl*  
 Объектную переменную, которая представляет **RDS. DataControl** объекта.  
  
## <a name="remarks"></a>Примечания  
 Сервер — это расположение где **RDS. DataControl** обработки запроса (то есть, запроса или обновления). По умолчанию, все запросы обрабатываются [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта, [MSDFMAP. Обработчик](../../../ado/guide/remote-data-service/datafactory-customization.md) компонента, и [MSDFMAP. INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md) файл на указанном сервере. Помните, что при изменении серверов для согласования параметров в старой и новой **MSDFMAP. INI** файлов. Несовместимость может привести к запросы, которые завершились успешно на одном сервере не работает на другой. Если свойство сервера присваивается пустая строка «», эти объекты будут использоваться на локальном компьютере.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Server (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [Свойство (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Свойство SQL](../../../ado/reference/rds-api/sql-property.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


