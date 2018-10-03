---
title: Настройка формата маршалинга Stream DCOM | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33359afb2910c75e34ff38c9606ff71b3760cbc1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802862"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Настройка формата маршалинга потока DCOM
Клиентский компьютер с помощью компонентов служб удаленных рабочих СТОЛОВ 1.5 или более ранней версии не совместим с сервером с помощью компонентов служб удаленных рабочих СТОЛОВ 2.0 или более поздней версии. При использовании в качестве базового протокола DCOM, поддержка для служб удаленных рабочих СТОЛОВ 2.0 или более поздней версии более эффективен при транспортировке [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов. Если ваш клиент работает компонентов служб удаленных рабочих СТОЛОВ 1.5 или более ранней версии, можно разместить сервер для работы с предыдущих поддержки служб удаленных рабочих СТОЛОВ (называемые 1.0 служб удаленных рабочих СТОЛОВ) или более поздней версии поддерживают служб удаленных рабочих СТОЛОВ (вызываемой RDS 2.0 или более поздней). Задайте следующие записи реестра:  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -или-  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```


