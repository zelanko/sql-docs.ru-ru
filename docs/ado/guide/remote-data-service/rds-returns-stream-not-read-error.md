---
title: RDS возвращает &quot;поток чтения не&quot; ошибка | Документы Microsoft
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
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d197487ed4d7e46d8e89b968c8fff4bcd9b80784
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>RDS возвращает &quot;поток чтения не&quot; ошибки
«Объект потока не удалось прочитать, так как он пуст или текущее положение находится в конце потока. Для потоков с пустым задайте текущую позицию в свойства Position. Чтобы определить, является ли пустой поток, проверьте свойство размера.»  
  
 Если вы видите это сообщение об ошибке, может предпринята попытка использования параметризованный запрос иерархических по протоколу http. Служб удаленных рабочих СТОЛОВ не позволяют использовать удаленный параметризованные иерархии.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


