---
title: "Шаг 3: Сервер получает набор записей (учебник служб удаленных рабочих СТОЛОВ) | Документы Microsoft"
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
- RDS tutorial [ADO], server obtains Recordset
ms.assetid: 9c6779c9-1208-4696-ac51-c39f3a6d9240
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62210ae4cbf206faebed32b87bdbf64edd3265d9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="step-3-server-obtains-a-recordset-rds-tutorial"></a>Шаг 3: Сервер получает набор записей (учебник служб удаленных рабочих СТОЛОВ)
Программа сервера использует текста строки и команда connect для запросов к источнику данных для нужные строки. ADO обычно используется для получения этого **записей**, несмотря на то, что другие Microsoft интерфейсы доступа к данным, таких как OLE DB, может быть использовано.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Программа пользовательского сервера может выглядеть следующим образом:  
  
```  
Public Function ServerProgram(cn as String, qry as String) as Object  
Dim rs as New ADODB.Recordset  
   rs.CursorLocation = adUseClient  
   rs.Open qry, cn   
   rs.ActiveConnection = Nothing  
   Set ServerProgram = rs  
End Function  
```  
  
## <a name="see-also"></a>См. также:  
 [Шаг 4: Сервер возвращает набор записей (учебник служб удаленных рабочих СТОЛОВ)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

