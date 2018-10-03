---
title: Свойство (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: abf2b751f6f1e89cf51560ad7e0d38aa05da7b8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851480"
---
# <a name="connect-property-rds"></a>Свойство Connect (служба удаленных рабочих столов)
Указывает имя базы данных, с которого запускаются операции запросов и обновлений.  
  
 Можно задать **Connect** во время разработки в [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) теги ОБЪЕКТОВ объекта, или во время выполнения в коде (например, VBScript) сценария.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Параметры  
 *connectionString*  
 Допустимая строка подключения. Дополнительные общие сведения о строках подключения см. в разделе [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства или к документации поставщика.  
  
> [!NOTE]
>  Указание в качестве поставщика для удаленного MS **RDS. DataControl** создаст сценарий четыре уровня. Сценарии, больше трех уровней не были протестированы и не должно возникнуть необходимости.  
  
 *DataControl*  
 Объектную переменную, которая представляет **RDS. DataControl** объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства (VBScript) Connect](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Метод запроса (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Обновите метод (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Метод SubmitChanges (служба удаленных рабочих столов)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


