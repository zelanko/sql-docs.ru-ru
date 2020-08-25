---
description: Свойство Server (служба удаленных рабочих столов)
title: Свойство сервера (RDS) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c7d2c095c9f10e95df54849ce729ffdcbbca135
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767523"
---
# <a name="server-property-rds"></a>Свойство Server (служба удаленных рабочих столов)
Указывает имя службы IIS (IIS) и протокол связи.  
  
 Свойство **сервера** можно задать во время разработки в тегах объектов[RDS. Объект элемента управления](./datacontrol-object-rds.md) , или во время выполнения в коде скрипта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
 **HTTP**  
  
 Синтаксис времени разработки  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 Синтаксис времени выполнения  
  
```  
  
DataControl  
.Server="https://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 Синтаксис времени разработки  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 Синтаксис времени выполнения  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 Синтаксис времени разработки  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 Синтаксис времени выполнения  
  
```  
  
DataControl.Server="computername"  
```  
  
 **Внутрипроцессно**  
  
 Синтаксис времени разработки  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 Синтаксис времени выполнения  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>Параметры  
 *авебсрвр*или *ComputerName*  
 **Строковое** значение, содержащее путь к Интернету или интрасети, или имя компьютера, если сервер находится на удаленном компьютере. или пустая строка, если сервер находится на локальном компьютере.  
  
 *port*  
 Необязательный элемент. Порт, используемый для подключения к серверу, на котором выполняются службы IIS. Номер порта задается в Internet Explorer (в меню **вид** выберите пункт **Параметры**, а затем перейдите на вкладку **Подключение** ) или в IIS.  
  
 *DataControl*  
 Объектная переменная, представляющая **RDS. Объект элемента управления** .  
  
## <a name="remarks"></a>Remarks  
 Сервер — это расположение, в котором **RDS. ** Обрабатывается запрос элемента управления (т. е. запрос или обновление). По умолчанию все запросы обрабатываются объектом [RDSServer.](./datafactory-object-rdsserver.md) DataObject, [мсдфмап. Компонент обработчика](../../guide/remote-data-service/datafactory-customization.md) и файл [MSDFMAP.INI](../../guide/remote-data-service/understanding-the-customization-file.md) на указанном сервере. Помните, что при изменении серверов для согласования параметров в старых и новых **MSDFMAP.INI** файлах. Несовместимость может привести к сбою запросов, успешно находящегося на одном сервере, на другом. Если для свойства сервера задана пустая строка "", эти объекты будут использоваться на локальном компьютере.  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства сервера (VBScript)](./server-property-example-vbscript.md)   
 [Свойство Connect (RDS)](./connect-property-rds.md)   
 [Свойство SQL](./sql-property.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](./submitchanges-method-rds.md)