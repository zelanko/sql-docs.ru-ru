---
title: "RDS возвращает &quot;поток чтения не&quot; ошибка | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd1d9232fd2fec4d3380ab037f8583b0047a5290
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot;поток чтения не&quot; ошибки
«Объект потока не удалось прочитать, так как он пуст или текущее положение находится в конце потока. Для потоков с пустым задайте текущую позицию в свойства Position. Чтобы определить, является ли пустой поток, проверьте свойство размера.»  
  
 Если вы видите это сообщение об ошибке, может предпринята попытка использования параметризованный запрос иерархических по протоколу http. Служб удаленных рабочих СТОЛОВ не позволяют использовать удаленный параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также:  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


