---
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
ms.openlocfilehash: 5cd4f578a8146a8fa7d45dcfd8e2b58f795def13
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82750854"
---
# <a name="server-property-rds"></a>Свойство Server (служба удаленных рабочих столов)
Указывает имя службы IIS (IIS) и протокол связи.  
  
 Свойство **сервера** можно задать во время разработки в тегах объектов[RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) , или во время выполнения в коде скрипта.  
  
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
  
 *порту*  
 Необязательный элемент. Порт, используемый для подключения к серверу, на котором выполняются службы IIS. Номер порта задается в Internet Explorer (в меню **вид** выберите пункт **Параметры**, а затем перейдите на вкладку **Подключение** ) или в IIS.  
  
 *DataControl*  
 Объектная переменная, представляющая **RDS. Объект элемента управления** .  
  
## <a name="remarks"></a>Remarks  
 Сервер — это расположение, в котором **RDS. **Обрабатывается запрос элемента управления (т. е. запрос или обновление). По умолчанию все запросы обрабатываются объектом [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) DataObject, [мсдфмап. Компонент обработчика](../../../ado/guide/remote-data-service/datafactory-customization.md) и [мсдфмап. INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md) -файл на указанном сервере. Помните, что при изменении серверов для согласования параметров в старом и новом **мсдфмап. INI** -файлы. Несовместимость может привести к сбою запросов, успешно находящегося на одном сервере, на другом. Если для свойства сервера задана пустая строка "", эти объекты будут использоваться на локальном компьютере.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства сервера (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [Свойство Connect (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Свойство SQL](../../../ado/reference/rds-api/sql-property.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


