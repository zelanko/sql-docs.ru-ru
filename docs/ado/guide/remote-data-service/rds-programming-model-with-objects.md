---
title: Модель программирования RDS с объектами | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2cfba2b659ed03f67d94c2c80812d7712e481f50
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704483"
---
# <a name="rds-programming-model-with-objects"></a>Модель программирования RDS с объектами
Цель служб удаленных рабочих СТОЛОВ — для получения доступа к и обновления источникам данных через посредника, такого как IIS. Модель программирования определяет последовательность действий, необходимых для достижения этой цели. Объектная модель задает объекты, методы и свойства влияют на модель программирования.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS позволяет выполнять следующие действия:  
  
-   Укажите программу для вызова на сервере, а также получить способ (прокси) для ссылки на него из клиента ([RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md)).  
  
-   Вызовите программу сервера. Передать параметры серверной программой, которая определяет источник данных и выдачи команд (прокси-сервера или [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)).  
  
-   Программа server получает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из источника данных, обычно с помощью ADO. При необходимости **записей** объект обрабатывается на сервере ([RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)).  
  
-   Программа server Возвращает конечное **записей** объект клиентскому приложению (прокси).  
  
-   На стороне клиента **записей** объект помещается в форму, можно легко использовать визуальные элементы управления (визуальному элементу управления и **RDS. DataControl**).  
  
-   Изменения в **записей** отправляются на сервер и используется для обновления источника данных объекта (**RDS. DataControl** или **RDSServer.DataFactory**).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о модели объектов служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-object-model-summary.md)   
 [Объект DataControl (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Объект DataSpace (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Сценарий RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Использование RDS и безопасность](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


