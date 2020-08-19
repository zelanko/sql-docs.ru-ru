---
description: Шаг 1. Укажите программу сервера (учебник по RDS)
title: Шаг 1. Указание серверной программы (учебник по RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b5c76aebd80ff4a5706c9226abc051c03940707
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451956"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Шаг 1. Укажите программу сервера (учебник по RDS)
В общем случае используйте [RDS. ](../../../ado/reference/rds-api/dataspace-object-rds.md) Метод [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) объекта Space для указания программы сервера по умолчанию, [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)DataObject или собственной пользовательской серверной программы (бизнес-объект). На сервере создается экземпляр серверной программы, и возвращается ссылка на серверную программу или *прокси*.  
  
 В этом руководстве используется серверная программа по умолчанию:  
  
```vb
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "https://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также:  
 [Шаг 2. вызов серверной программы (учебник по RDS)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
