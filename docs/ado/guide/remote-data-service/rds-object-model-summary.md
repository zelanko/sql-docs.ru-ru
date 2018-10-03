---
title: Сводка по модели объектов служб удаленных рабочих СТОЛОВ | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0421f5eead03d6e3641054b9c26dc1d4dac838e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822134"
---
# <a name="rds-object-model-summary"></a>Сводка объектной модели RDS
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Объект|Описание|  
|------------|-----------------|  
|[RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md)|Этот объект содержит метод для получения прокси-сервера. Прокси-сервер может быть значение по умолчанию или пользовательский сервер программу (бизнес-объекта). Программа server могут быть вызваны в Интернете, интрасети, локальной сети или быть локальную библиотеку динамической компоновки.<br /><br /> **DataSpace** объект безопасен для скриптов.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Этот объект представляет серверной программы по умолчанию. Он выполняет поведение по умолчанию служб удаленных рабочих СТОЛОВ данных извлечения и обновления.<br /><br /> **DataFactory** объект не является безопасным для использования в сценариях.|  
|[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Этот объект автоматического вызова **RDS. Пространство данных** и **RDSServer.DataFactory** объектов.<br /><br /> Этот объект можно используйте для вызова по умолчанию поведение получения или обновления данных служб удаленных рабочих СТОЛОВ.<br /><br /> Этот объект также предоставляет средства для визуальных элементов управления для доступа к возвращенного **записей** объекта.<br /><br /> **DataControl** объект безопасен для скриптов.|  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Сценарий RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Использование RDS и безопасность](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


