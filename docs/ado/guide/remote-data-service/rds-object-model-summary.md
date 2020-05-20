---
title: Сводка объектной модели RDS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 95ddd84bfd755e044d97a6043f295014933ae18c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763595"
---
# <a name="rds-object-model-summary"></a>Сводка объектной модели RDS
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Объект|Описание|  
|------------|-----------------|  
|[Клиент. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md)|Этот объект содержит метод для получения прокси сервера. Может использоваться прокси-сервер по умолчанию или пользовательская программа (бизнес-объект). Серверная программа может быть вызвана в Интернете, интрасети, локальной сети или в виде локальной библиотеки динамической компоновки.<br /><br /> Объект **Space** является надежным для скриптов.|  
|[RDSServer. факт.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Этот объект представляет программу сервера по умолчанию. Он выполняет получение данных RDS по умолчанию и поведение обновления.<br /><br /> Объект **фактов** не является надежным для сценариев.|  
|[Клиент. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Этот объект может автоматически вызывать **RDS. Объекты Space** и **RDSServer. объект фактов** .<br /><br /> Используйте этот объект, чтобы вызвать получение данных RDS по умолчанию или поведение обновления.<br /><br /> Этот объект также предоставляет средства визуальных элементов управления для доступа к возвращенному объекту **набора записей** .<br /><br /> Объект " **элемент управления** " является надежным для сценариев.|  
  
## <a name="see-also"></a>См. также  
 [Основы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Сценарий RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Руководство по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Использование RDS и безопасность](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


