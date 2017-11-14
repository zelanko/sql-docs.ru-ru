---
title: "Модель программирования служб удаленных рабочих СТОЛОВ с объектами | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f89c867cb836ec69fd5fe59adf16d93f4708d0f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="rds-programming-model-with-objects"></a>Модель программирования служб удаленных рабочих СТОЛОВ с объектами
Службы удаленных рабочих столов предназначена для того, чтобы получить доступ к и обновление источников данных через посредника, такими как службы IIS. Модель программирования определяет последовательность действий, необходимых для достижения этой цели. Объектную модель указывает объекты, методы и свойства, влияющие на модели программирования.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Служб удаленных рабочих СТОЛОВ позволяет выполнить следующую последовательность действий:  
  
-   Укажите программу для вызова на сервере и получить способом (прокси) для ссылки на него из клиента ([RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md)).  
  
-   Необходимо вызовите программу сервера. Передать параметры серверной программой, которая определяет источник данных и команды для выдачи (прокси-сервера или [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)).  
  
-   Программа сервер получает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из источника данных, обычно с помощью ADO. При необходимости **записей** объект обрабатывается на сервере ([RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)).  
  
-   Программа server Возвращает конечное **записей** объекта клиентскому приложению (прокси).  
  
-   На стороне клиента **записей** объект помещается в форму, которую можно легко использовать визуальные элементы управления (визуальному элементу управления и **RDS. DataControl**).  
  
-   Изменения **записей** отправляются обратно на сервер и используется для обновления источника данных объекта (**RDS. DataControl** или **RDSServer.DataFactory**).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о модели объектов служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-object-model-summary.md)   
 [Объект DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Объект пространства данных (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Сценарии служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Учебник служб удаленных рабочих СТОЛОВ](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Использование RDS и безопасность](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



