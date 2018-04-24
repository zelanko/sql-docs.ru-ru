---
title: 'Шаг 1: Укажите программу Server (учебник служб удаленных рабочих СТОЛОВ) | Документы Microsoft'
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
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c47ebabbb0560dafba7582714759f619f2438d24
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Шаг 1: Укажите программу Server (служб удаленных рабочих СТОЛОВ учебник)
В общем случае использовать [RDS. Пространство данных](../../../ado/reference/rds-api/dataspace-object-rds.md) объекта [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) метод, чтобы указать программу по умолчанию сервера [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), или собственную программу на другой сервер (бизнес-объекта). Программа server создается на сервере и ссылку на программу сервера или *прокси-сервера*, возвращается.  
  
 В этом учебнике используется серверной программы по умолчанию:  
  
```  
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Шаг 2: Вызвать программу Server (служб удаленных рабочих СТОЛОВ учебник)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
