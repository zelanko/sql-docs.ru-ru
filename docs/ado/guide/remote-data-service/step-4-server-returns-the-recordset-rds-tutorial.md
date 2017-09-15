---
title: "Шаг 4: Сервер возвращает набор записей (учебник служб удаленных рабочих СТОЛОВ) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1cc20f813b87432ede6f0ecf98cd1dd41bd526fd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Шаг 4: Сервер возвращает набор записей (учебник служб удаленных рабочих СТОЛОВ)
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Преобразует полученный служб удаленных рабочих СТОЛОВ **записей** объекта в форму, которое может быть отправлено обратно клиенту (то есть он *выполняет маршалинг* **записей**). Точная форма нового преобразования и способ передачи зависит ли сервер в Интернете или интрасети, локальной сети, или библиотеки динамической компоновки. Тем не менее эта информация не является критически важным; все, что имеет значение, RDS отправляет **записей** обратно клиенту.  
  
 На стороне клиента **записей** объект возвращается и присваивается локальной переменной.  
  
```  
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>См. также:  
 [Шаг 5: DataControl годным внесенные (учебник служб удаленных рабочих СТОЛОВ)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

