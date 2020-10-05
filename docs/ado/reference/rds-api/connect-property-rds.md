---
description: Свойство Connect (служба удаленных рабочих столов)
title: Свойство Connect (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: rothja
ms.author: jroth
ms.openlocfilehash: 5387745648b4aafa1db9964a8b82d8aa403e8473
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722515"
---
# <a name="connect-property-rds"></a>Свойство Connect (служба удаленных рабочих столов)
Указывает имя базы данных, из которой выполняются операции запроса и обновления.  
  
 Свойство **Connect** можно задать во время разработки в [RDS. Теги объекта элемента управления](./datacontrol-object-rds.md) DataObject или во время выполнения в коде скрипта (например, VBScript).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectionString*  
 Допустимая строка подключения. Дополнительные общие сведения о строках подключения см. в описании свойства [ConnectionString](../ado-api/connectionstring-property-ado.md) или документации поставщика.  
  
> [!NOTE]
>  Указание MS Remote в качестве поставщика для **RDS. Элемент управления** "набором событий" создает сценарий из четырех уровней. Сценарии более трех уровней не были протестированы и не должны быть нужны.  
  
 *DataControl*  
 Объектная переменная, представляющая **RDS. Объект элемента управления** .  
  
## <a name="applies-to"></a>Применение  
 [Объект DataControl (служба удаленных рабочих столов)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Connect (VBScript)](./connect-property-example-vbscript.md)   
 [Метод query (RDS)](./query-method-rds.md)   
 [Метод Refresh (RDS)](./refresh-method-rds.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](./submitchanges-method-rds.md)