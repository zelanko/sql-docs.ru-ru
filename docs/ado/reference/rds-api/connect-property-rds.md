---
title: Свойство (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f30b087323ddfc26297844209d7293ea40ed5604
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connect-property-rds"></a>Свойство (RDS)
Указывает имя базы данных, из которой выполняются операции запроса и обновления.  
  
 Можно задать **Connect** во время разработки в [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта тегов ОБЪЕКТОВ, или во время выполнения в коде (например, VBScript) сценария.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Параметры  
 *connectionString*  
 Допустимая строка подключения. Дополнительные общие сведения о строках соединения см. в разделе [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства или к документации поставщика.  
  
> [!NOTE]
>  Укажите удаленный MS как поставщик для **RDS. DataControl** создаст сценарий четыре уровня. Сценарии, больше трех уровней не были проверены и не требуется.  
  
 *DataControl*  
 Объектную переменную, которая представляет **RDS. DataControl** объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства (VBScript) подключения](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Метод запроса (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Обновить метод (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


