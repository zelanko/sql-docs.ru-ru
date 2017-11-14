---
title: "Настройка DCOM поток маршалинг формат | Документы Microsoft"
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
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: abc77e2e56ec8251e158121ca8bb6083641d4cb3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setting-dcom-stream-marshaling-format"></a>Настройка DCOM поток маршалинг формата
Клиентский компьютер с помощью компонентов служб удаленных рабочих СТОЛОВ 1.5 или более ранней версии не совместим с сервером с помощью компонентов служб удаленных рабочих СТОЛОВ 2.0 или более поздней версии. При использовании в качестве базового протокола DCOM, поддержка для служб удаленных рабочих СТОЛОВ 2.0 или более поздней версии более эффективна при транспортировке [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов. Если клиент работает под управлением компоненты служб удаленных рабочих СТОЛОВ 1.5 или более ранней версии, можно установить сервер для работы с предыдущей Поддержка служб удаленных рабочих СТОЛОВ (называемые 1.0 служб удаленных рабочих СТОЛОВ) или более поздней версии поддерживают служб удаленных рабочих СТОЛОВ (вызываемой RDS 2.0 или более поздней версии). Задайте одно из следующих записей реестра.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -или-  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```



